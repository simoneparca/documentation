## Tasti rapidi

CTRL+ALT+F1-F6 terminali, CTRL+ALT+F7-F8 xterminal (or AlT+F7-F8)

# A linux Jurney

L'idea del software libero mi piace tantissimo, per me è il futuro. Però oggi... è un disastro.
Ho fatto le prime prove con linux alla fine del vecchio millennio, allora la distribuzione più diffusa era slackware, nascevano KDE e subito dopo Gnome, non c'era ancora la banda larga, e sono andato a qualche incontro nei lug, dove le domande erano qualcosa tipo: ma come faccio a spengnere linux? già, a quei tempi anche spegnere il computer non era banale. e la risposta non era certo semplice come premere un bottone. Figuriamocu poi quando si parlava di periferiche USB, drivers, ecc. E neanche a dirlo il desktop grafico era tutto da configurare, col cavolo che partiva di default.
Alla fine ho lasciato perdere per un pò, i tempi non erano maturi.

## 2019-12-26

In varie occasioni ho riprovato a fare qualche esperimento con linux, ma questa volta ci ho provato con maggiore impegno.
Ho messo alla prova varie distribuzioni, alla ricerca di quella più snella, semplice ma al tempo stesso sufficientemente usabile.
Facendo prove su macchine virtuali virtualBox, ho monitorato alcuni parametri:
- Disco: spazio su disco occupato alla fine dell'installazione, in Gb
- Memoria: Ram utilizzata appena finto il boot (Memoria usata + cache usata) in Mb
- Boot: Secondi necessari prima di avere una GUI che risponsiva
- Autorun: inserito un CD, viene montato ed eseguito automaticamente?
- Gcc: il compilatore è incluso?
- Tile: è possibile con pochi movimenti affiancare 2 finestre?

Non sono certo parametri di giudizio esaustivi, ma almeno sono parametro oggettivi e riproducibili.

|                 | Disco | Memoria | Boot | Autorun | Gcc | Tile | Note                         |
|-----------------|-------|---------|------|---------|-----|------|------------------------------|
| Kubuntu         | 12    | 430+800 | 70   | No      | No  | Si   | Ricorda le app aperte        |
| Ubuntu          | 10    | 620+775 | 70   | Si      | No  | Si   |                              |
| Lubuntu 19 LXQt | 9     | 300+500 | 50   | No      | No  | No   |                              |
| Mint Cinnamon   | 10    | 520+570 | 55   | Si      | No  | Si   | 2 crash in breve tempo       |
| Mint Mate       | 10    | 425+670 | 50   | Si      | Si  | Si   |                              |
| Fedora Gnome    | 12    | 830+826 | 75   | Si      | Si  | Si   | Senza conf fatte sugli altri |
| MX Xfce         | 11    | 430+630 | 45   | No      | Si  | Si   | Senza conf fatte sugli altri |
| Lubuntu 18 LXDE | 10    | 250+450 | 35   | No      | No  | No   | Senza conf fatte sugli altri |
| Mint Xfce       | 12    | 450+650 | 40   | No      | Si  | Si   | 2 crash                      |

Alla fine ho scelto Mint con ambiente grafico xfce. Avrei potuto scegliere MX, ma l'ho trovata troppo complicata, o Kubuntu, che magari era un pò più lenta ma comunque più ricca anche se un pò più lenta.
quindi per dare un consigio rapido a chi deve scegliere una distribuzione:
- Kubuntu se hai un computer veloce
- Mint Xfce se hai un computer lento
- MX se sei uno smanettone.
Il livello non è certo quello di Windows 10, direi che linux è indietro almeno di 15 anni, al momento; ma ha raggiunto un livello accettabile.

## 2020-04-24 Linux ai tempi del corona Virus

Dopo un pò di utilizzo di linux in macchine virtuali, decido di rivitalizzare il mio vecchio PC Pentium 4 installando linux. Non ha neanche il boot USB, e non avendo vogli di sprecare tempo a masterizzare DVD, procedo alle installazioni con UnetBootIn.
dispongo di 3 dischi, uno IDE principale, su cui lascio Windows XP, e due dischi sata, configurati in RAID0, dove andrò ad installare linux.
La delusione inizia prima di iniziare: Ubuntu terminerà presto il supporto per le piattaforme 32bit. Ma come, tutta la storia di linux che rivittalizza vecchi pc... vabbè.
Kubuntu 18LTS, ultima versione disponibile a 32Bit, va in crash prima di finire il setup.

Il problema sembra essere il driver video (ho una ATI 7000)
https://wiki.debian.org/it/AtiHowTo
https://wiki.ubuntu-it.org/Hardware/Video/Amd
https://wiki.ubuntu-it.org/Hardware/Video/Amd/Amdgpu
https://wiki.ubuntu-it.org/Hardware/Video/Amd/Radeon
https://www.amd.com/en/support/kb/release-notes/rn-rad-lin-19-50-unified
https://amdgpu-install.readthedocs.io/en/latest/

[AMD Catalyst™ 15.9 Proprietary Linux Graphics Driver Release Notes _ AMD.html]
[https://www.amd.com/en/support/kb/faq/gpu-630](AMD Radeon™ Software Support for Legacy Graphics Products)
Vorrei provare con le versioni indicate compatibili con la mia scheda video, ma 
Ubuntu 12-15 
- Red Hat Enterprise Linux Suite 7.1, 7.0, 6.6, 6.5
- Ubuntu 12.04.4 LTS, 14.04.2, 15.04 Kubuntu non sono più disponibili online
- SUSE® Linux Enterprise 11 SP3, 12
- OpenSuSE 13.1
Distribution specific packages are available for:
- Red Hat Enterprise Linux Suite 7.1, 7.0, 6.6, 6.5
- Ubuntu 12.04.4 LTS, 14.04.2

In ulteriori letture mi sembrava di aver letto che ATI non è compatibile con Gnome, ma non mi sono segnato il link.

Provate tutte le distribuzioni Ubuntu dalla 12 alla 18, e anche debian 10 senza successo. Alla fine provata Mint xfce, e tutto sembra funzionare.

### System Requirements
Before attempting to install the AMD Catalyst™ Proprietary Linux Graphics Driver, the following software must be installed:
- Xorg/Xserver 7.4 and above (up to 1.17)
- Linux kernel 2.6 or above (up to 3.19)
- glibc version 2.2 or 2.3
- POSIX Shared Memory (/dev/shm) support is required for 3D applications
NOTE: If a Linux 2.6.11 or newer kernel was built with CONFIG_AGP enabled, the kernel AGP frontend is required to load the fglrx kernel module. To identify whether your kernel with CONFIG_AGP enabled, look for CONFIG_AGP=y in the kernel config file, or if the 'agpgart' module is loaded

The following packages must be installed in order for the AMD Catalyst™ Proprietary Linux Graphics Driver to install and work optimally:
- gimp-help-en
- gimp-help-common
- XFree86-Mesa-libGL
- libstdc++
- libgcc
- XFree86-libs
- fontconfig
- freetype
- zlib
- gcc

#### Problema subwoofer non funzionante
/etc/pulse/daemon.conf  change it to this:
enable-lfe-remixing = yes

# Riferimenti utili

## https://developers.redhat.com/
- [Get Started](https://developers.redhat.com/products/rhel/hello-world#fndtn-windows)
- [Cheat Sheet](RHEL8_CheatSheet.pdf)

### Misc
- https://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/