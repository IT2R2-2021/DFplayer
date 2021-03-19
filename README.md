# DFPlayer

Utilisation de la tâche DFPlayer :

Envoyer par message MailBox le numéro du son à jouer, puis avec un event lancer la tâche DFPlayer.

Numéro des différent sons :

klaxon -> 0x00
bip    -> 0x00

Liaison série UART data :

Format : $S VER Len CMD Feedback para1 para2 checksum1 checksum2 $0
$S -> 0x7E  || Start byte
VER -> 0xFF || Version
Len -> 0x06 || 6 bytes not counting start, end and verification.
CMD -> Commande || source=0x09 ; volume=0x06 ; track=0x03 ; playback=0x0D
Feedback -> Si feedback 0x01 sinon 0x00
para1 -> paramètre 1 high data byte (souvent 00)
para2 -> paramètre 2 low data byte 
checksum1 -> addition des byte not including start byte, high data byte
checksum2 -> addition des byte not including start byte, low data byte
$0 -> 0xEF ||End byte
