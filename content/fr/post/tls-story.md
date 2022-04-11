---
date: 2022-04-04T12:00:0+01:00
description: "C'est l'histoire d'un secret"
tags: ["tls","golang","cryptographie"]
title: "Il était une fois TLS"
---

Notes:

# Intro

Les débats lors des développements sont monnaie courante, d'autant plus lors de sujets tels que la sécurité.
Lors d'un travail sur la mise en place d'une communication sécurisée,
nous avons entamé une discussion sur la configuration d'une clé de chiffrement.
Notre insatiable curiosité technique étant au moins aussi importante que notre soif de débats,
je décidais alors de me lancer dans la découverte de ces concepts.
J'étais bien loin de me douter qu'un monde entier aller s'ouvrir devant moi.

N'ayez crainte, aussi complexe et étendu soit notre objectif, un voyage commence toujours par un premier pas.
Je vous propose de vous emmener découvrir la cryptographie, cet art de rendre un message secret, à travers l'histoire.
Chemin faisant, nous observerons les concepts sous-jacents,
nous jouerons avec ces mécanismes au traver d'anecdote historique, 
et nous verrons son évolution jusqu'à nos jours.
Je vous en prie, venez, le voyage commence.

# Premier Pas

## Pourquoi

Le besoin de ne rendre compréhensible un message seulement pour qui-de-droit est probablement aussi ancien que la communication elle-même.
Lorsque l'on parle de message secret, il vous vient peut-être l'image d'agent secret et de code sur microfilm, ce qui est, nous le verrons, parfaitement valide.
Mais il peut s'agir également d'une méthode pour protéger un savoir,
un procédé de fabrication ou même des textes religieux.
Pour les plus romantiques, il peut s'agir de protéger une communication épistolaire d'un amour interdit.
De nos jours, il s'agit de protéger les milliards de communications effectuées chaque jour dans le monde.
Quoi qu'il en soit, les motivations d'utiliser la cryptographie sont nombreuses et variées.

## Comment

Pour rendre un message secret, nous pouvons :
* substitution par caractère, il s'agit du *chiffrement* (ex: remplacer par la lettre suivante dans l'alphabet).
* substitution par mot, il s'agit du *codage* (ex: traduire dans une autre langue)
* dissimuler son existence même, il s'agit de la *stéganographie* (ex: [l'encre invisible](https://fr.wikipedia.org/wiki/Encre_invisible))

Par la suite, nous parlerons de chiffrement et de message chiffré par souci de simplicité. //améliorer

Nous avons maintenant un mobile et un peu de vocabulaire, partons sur les sentiers de l'histoire.

## De l'antiquité à nos jours

D'un point de vue historique, seul les écrits laissent une trace dans le temps.
Il est probable que certains textes datant de plus de 4500 ans ait été modifié pour se soustraite aux regards indiscrets ou simplement dans le cadre d'une pratique religieuse..
// notes: Trouver les sources. 
Nous avons des traces de tablettes Babyloniens, datées de 2500 ans av J.C. modifiés pour protéger un secret de fabrication artisanal.
Il ne s'agit ici que d'une suppression de voyelles sur certaines occurrences et de l'utilisation de caractères non communs.

// notes
Tout d'abord communication, besoin de transmettre un message de facon sécurisé (religion, amour, guerre)
Arrivée du chiffrement (Code caesar/rot? baton, enigma? Petite frise avec les "codes")

Retour sur internet, création HTTP & contexte échanges publics.
Besoin de confidentialité arrivée SSL (vérifier historique et étapes)
Arrivée de TLS

## L'origine

Il existe des textes 



# Les mains dans le cambouis

Utilisation openssl & langage Go (ou juste le go a voir)
CA (root, intermediates)
Certificate chaining
CSR
certificats
per/der
Comment est valider le certificat ? Browser & code.
CRL

PKI
Cipher Suites
Compression Methods
Extensions Length
SNI
OCSP
Supported Groups
Elliptic curves
Signature Algorithms
Renegotiation Info
SCT

Limitations
    techniques
    légales
mTLS
Gérer ses certificats

DNS over TLS (DoT)
DNS over HTTPS (DoH)

DTLS 

ktls

bpf

Et apres ? (nouvelles technologies/ processeurs quantiques)

# References

outils
protocols
algorithms
articles 
rfc

# Conclusion

D'hier à aujourd'hui meme besoin, outils différents. Puissance de calcul et importance des mathématiques, et demain xxxxx


https://tls.ulfheim.net/
https://geekflare.com/tls-101/
https://www.amazon.fr/Codage-cryptographie-Math%C3%A9maticiens-espions-informatiques/dp/B00T7CNP8G
