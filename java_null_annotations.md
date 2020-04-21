# Eliminare l'errore Null pointer exception

It seems that the concept of null references exists thanks to Tony Hoare.
The concept of null was introduced in the Algol language, and later Sir Hoare called it “my billion-dollar mistake”.

Ci sono vari pattern per evitre l'uso di null, non oggetto di questo articolo. Nonostante questi pattern, esistono casi in cui è comodo e corretto usare i riferimenti null.
Ma se NullPointerException non è l'errore più frequente, è sicuramente uno dei più diffusi. La buona notizia è che è possibile evitarlo, definitivamente e con certezza matematica, con l'ausilio dell'analisi statica del codice.
Inizialmente si potrebbe pensare che "basta controllare che un riferimento sia non null prima di usarlo", e in effetti per molti anni si è seguita questa strada, con i risultati sotto gli occhi di tutti. Il vero problema è sapere quando davvero questi controlli vanno fatti: aggiungerli sempre, nel dubbio, non è una soluzione buona, non solo perchè il codice sarebbe pieno di controlli inutili, ma soprattutto perchè, bisognerebbe decidere cosa fare per ogni singolo controllo che fallisce. Facciamo un esempio:
<pre><code>
for (String s : getSomeStrings()) {
    useSomeString(s);
}
</code></pre>
Innanzi tutto getSomeStrings() potrebbe tornare null. certo, il buon senso dice che se ritorna una collezione iterabile, probabilmente ritorna una lista vuota anzichè null, ma ne sei certo? aggiungiamo un controllo? e già che ci siamo, chi ci dice che i valori della lista non siano null?
<pre><code>
List<String> l = getSomeStrings();
if (l!=null) {}
    for (String s : l) {
        if (s!=null) {
            useSomeString(s);
        } else {
            // ????
        }
    }
} else {
    // ????
}
</code></pre>
E già così, il codice è pressochè raddoppiato, e non abbiamo ancora gestito cosa fare nel caso si incontrasse un null. Andrà sempre bene andare avanti senza fare quello che andava fatto? No, probabilmente bisognerà generare errori o implementare logiche alternative. Oppure... si va a controllare cosa fa la funzione, com'è implementata; se non sono disponibili i sorgenti, forse c'è una buona documentazione; le buone norme dicono che se viene tornato un valore null, dovrebbe essere documentato! Speriamo! In questo mondo di dubbi e speranze (spesso infrante con il fatidico errore) la cosa migliore è avere una conoscenza quanto più precisa possibile di cosa può essere null, e cosa non può esserlo. Perchè tenere questa conoscenza a mente, o lasciarla in vaghe frasi nella documentazione? mettiamola in chiaro! per esempio con una <b>Annotazione</b>
<pre><code>
@Nonnull List<@Nullable String> getSomeStrings()
</code></pre>
Si può anche fare di meglio, visto che la maggior parte delle variabili non saranno nulle: si può annotare l'intera classe, o l'intero package, come @NonNullByDefault. In questo modo le annotazioni necessarie saranno davvero poche, ma adesso sappiamo chiaramente cosa dobbiamo controllare e cosa no. Ma la cosa più bella è che il nostro codice può essere analizzato staticamente da uno strumento che ci dice se abbiamo implementato tutti i controlli necessari o se ne abbiamo implementati di inutili.

Ma il caso peggiore, secondo me, non sono i valori che ci vengono ritornati, ma i valori che noi passiamo ad altre funzioni. Che facciamo se useSomeString(String) non accetta un parametro null? evitiamo di chiamarla del tutto? andrà bene chiamarla con valori di default? quali? In questo caso mi sembra evidente che "non basta controllare che sia null", quindi è meglio saperlo con certezza.

Facciamo un altro esempio:
<pre><code>
String result=null;
for (s: getSomeStrings())
    if (s!=null) {
        result=s;
        break;
    }
}
useSomeString(result.toUpperCase());
return;
</code></pre>
Qui qualcuno potrebbe obiettare: se uso le annotazioni, un controllo formale segnalerà un potenziale errore, ma sono sicuro che non c'è nesssun errore. Non voglio segnalazioni inutili!
 - Prima di tutto, se annoti, non significa che devi per forza attivare anche il controllo formale (di solito si lancia un tool, o si abilita un'opzione nell'IDE) Il valore informativo delle annotazioni sarà comunque utile, come una buona documentazione, ma espressa in modo più chiaro e standard.
 - Il vero problema non è il controllo formale, è che il tuo codice potrebbe essere scritto meglio:
<pre><code>
for (s: getSomeStrings())
    if (s!=null) {
        useSomeString(s.toUpperCase());
        return;
    }
}
</code></pre>
Spesso si emettono giudizi soggettivi sulla qualità del codice: è illeggibile, è scritto male, è contorto, ecc.

Possiamo ora finalmente dare una definizione più oggettiva di codice ben scritto: quello che non solleva avvisi: grazie alle annotazioni e i controlli statici e formali, abbiamo un metro di giudizio non esaustivo, ma per lo meno oggettivo. Senza annotazioni, discutere su quale delle due implementazioni precedenti sia migliore, potrebbe essere una discussione senza fine. A mio avviso la seconda soluzione è migliore comunque, se non altro più compatta, ma vallo a far capire a chi ha scritto la prima (è un esempio tratto da casi reali, scritti da colleghi).

Evitare i null pointer è solo il primo passo. L'uso delle annotazioni ci  costringe a scrivere codice in modo diverso, più lineare e chiaro, evitando costrutti nei quali il compilatore
non riesce a garantire la correttezza. Se non ci riesce il compilatore, forse non ci riusciranno neanche i
vostri colleghi, non subito, per lo meno. Chi, come me, ha fatto l'esperienza di aggiungere questi controlli a codice esistente noterà che spesso bisogna riorganizzare il codice (in meglio) per aiutare il compilatore a garantire
l'essenza di errori, e oltre a rimuovere nullPointerException scoprirete e rimuoverete molti altri errori; infine, per prevenire queste situazioni, smetterete di usare molti costrutti contorti e poco leggibili; e forse diventerete programmatori migliori. Provare per credere.

Alcuni aticoli a riguardo:

#### https://blog.jooq.org/2016/11/24/the-java-ecosystems-obsession-with-nonnull-annotations/

Questo articolo sostiene che l'uso delle annotazioni è inutile e pensante, ma le argomentazioni secondo me dovute alla mancata conoscenza ed esperienza dell'argomento. Non è assolutamente vero che bisogna riempire il codice di annotazioni: non tiene conto del fatto che è possibile aggiungere un'annotazione che rende tutte le variabili non null per default, semplificando notevolmente la sintassi. Inoltre non tiene conto del fatto chè è possibile usarle solo quando si ritiene necessario. Perchè privarsi quindi di uno strumento opzionale? In attesa di una vera valutazione quantitativa dei costi/benefici, molto difficile da fare, secondo me bisogna per lo meno lasciare la libertà di scelta caso per caso. 

Facciamo un'analogia, si pensi al fatto che in quasi tutti i linguaggi bisogna dichiarare esplicitamente il tipo delle variabili, tutte le variabili. In linguaggi come visual basic 6.0, invece, non era necessario. Con analogia con il nostro caso, qualcuno avrà sicuramente pensato che dichiarare il tipo per ogni variabile era come usare la bomba atomica per nulla. La storia dei linguaggi di progammazione ci insegna che chi pensava così, aveva torto; anche ogni buon programma visual basic cominciava con la riga:
<code>Option Explicit On</code> che forzava la necessità di dichiarare il tipo, per rendere più robusto il programma ed evitare inevitabili errori che, con ingenuità, si potrebbe pensare che sarebbero stati facili da evitare.  
Con le null annotation la storia si ripete, solo che ora tutto è più semplice perchè non bisogna aggiungere una parola chiave ad ogni variabile, visto che si può assumere che la maggior parte siano non nulle, basta annotare con un semplice @Nullable quelle che potranno essere nulle, che statisticamente sono una piccola minoranza.

- https://stackoverflow.com/questions/4963300/which-notnull-java-annotation-should-i-use
- 2012-11-20 https://stackoverflow.com/questions/13484202/how-to-use-nullable-and-nonnull-annotations-more-effectively
- https://www.baeldung.com/spring-null-safety-annotations
- https://blog.jetbrains.com/dotnet/2018/08/13/null-pointers-opportunity-not-exception-code-smells-series/
