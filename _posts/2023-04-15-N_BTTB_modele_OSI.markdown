---
layout: post
title:  'Network - Back To The Base - Introduction au modèle OSI'
---

# Introduction
Dans les réseaux informatiques, les différents noeuds connectés à un même réseau ont besoin de communiquer entre eux. Pour cela, des standards ont été définis. Cela permet de communiquer de façon normée. Cependant, la façon dont a été implémenté ces protocoles fonctionne par couches. Chacune de ces couches possède des protocoles différents pour fonctionner. 
Dans cet article, nous allons voir ces différentes couches, comments elles fonctionnent entre elles, et des exemples de protocoles et de cas d'usage pour chacune d'entre elles.

# Le modèle
Le modèle OSI a été défini par une norme ISO dans la fin des années 1970, et il est toujours utilisé de nos jours malgré les évolutions technologiques qui ont eu lieu depuis.
Il se décompose en 7 couches :
Physique
Liaison
Réseau
Transport
Session
Présentation
Application

## 1 - Physique
Cette couche permet de communiquer de façon concrète les informations : elles sont transformées sous forme de bits en utilisant différents mécanisme en fonction du média physique utilisé : des signaux électriques pour des câbles ethernet, des signaux lumineux pour des fibres optiques, des ondes pour les média Radio.

## 2 - Liaison
La couche de laison permet à deux machines directement connectées de communiquer entre elles. Pour communiquer, les noeuds utilisent leur adresse physiques, courament appelées Adresse MAC. 

## 3 - Réseau
Cette couche sert à acheminer la donnée d'un noeud à un autre lorsque ceux-ci ne sont pas directement connectés. C'est à ce niveau que réside le protocole IP. A ce niveau du modèle, les noeuds communiquent avec une adresse IP et non leur adresse MAC.

## 4 - Transport
Le transport permet de gérer le contrôle du flux. Plusieurs protocoles tels que TCP ou UDP peuvent être utilisés. Tous n'ont pas les mêmes fonctionnalités ou la même résilience à la perte ou l'altération de paquets. En fonction des besoins, un protocole différent sera utilisé.
La couche transport ajoute également la notion de port pour la plupart des protocoles de cette couche. 
Note : le protocole ICMP est considéré comme un protocole de couche 3 car il est défini comme partie intégrante du protocole IP par sa RFC, mais implémenté comme un protocole de couche 4 sans notion de port [source](https://www.rfc-editor.org/rfc/rfc792).

## 5 - Session
La couche session permet de gérer l'établissement d'une session, cette fait l'intermédiaire avec la couche 7 pour toute la durée de la session. Elle peut également permettre de récupérer des sessions qui auraient pu tomber en time-out pour reprendre là où la communication s'était arrêtée. Ces fonctionnalités peuvent également être gérée directement au niveau applicatif selon les protocoles utilisés. Les protocoles courants de cette couche sont : NetBIOS, L2TP, PPTP, H.245, RTCP, RPC, SMPP.

## 6 - Présentation
La couche de présentation sert à formater les données, et éventuellement les transformer. C'est dans cette couche qu'interviennent le chiffrement (avec TLS par exemple) ou la compression des données. C'est aussi là que les données peuvent être sérialisés en utilisant des formats de données tels que JSON ou XML.

## 7 - Application
La couche application est probablement celle qui contient le plus de protocoles connus : HTTP, HTTPS, DNS, FTP, SMTP, LDAP, la liste est longue.
Cette couche contient les protocoles qui délivrent le service souhaité, les autres couches (1 à 6) étant un moyen d'arrive à la couche 7. 


# La communication