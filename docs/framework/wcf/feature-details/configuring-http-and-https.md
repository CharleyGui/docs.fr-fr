---
title: Configuration de HTTP et HTTPS
description: Découvrez comment configurer HTTP/HTTPs pour permettre aux services WCF et aux clients de communiquer. Configurez une inscription d’URL et une exception de pare-feu à l’aide de Netsh.exe.
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: fbff78ff8e2c5c4fa73a56a3fdc15163596aa985
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245139"
---
# <a name="configuring-http-and-https"></a>Configuration de HTTP et HTTPS

Les services et les clients WCF peuvent communiquer sur HTTP et HTTPS. Les paramètres HTTP/HTTPS sont configurés à l'aide d'IIS (Internet Information Services) ou d'un outil de ligne de commande. Lorsqu'un service WCF est hébergé sous IIS, des paramètres HTTP ou HTTPS peuvent être configurés dans IIS (avec l'outil inetmgr.exe). Si un service WCF est auto-hébergé, les paramètres HTTP ou HTTPS sont configurés à l'aide d'un outil de ligne de commande.

Au minimum, vous souhaitez configurer une inscription d’URL et ajouter une exception de pare-feu pour l’URL que votre service utilisera. Vous pouvez configurer ces paramètres à l’aide de l’outil Netsh.exe.

## <a name="configuring-namespace-reservations"></a>Configuration des réservations d’espaces de noms

La réservation d'espace de noms assigne les droits d'une partie de l'espace de noms de l'URL HTTP à un groupe d'utilisateurs particulier. Une réservation leur donne le droit de créer des services qui écoutent sur cette partie de l'espace de noms. Les réservations sont des préfixes d’URL, ce qui signifie que la réservation couvre tous les sous-chemins du chemin de réservation. Les réservations d'espace de noms autorisent deux façons d'utiliser des caractères génériques. La documentation de l’API du serveur HTTP décrit l' [ordre de résolution entre les revendications d’espace de noms qui impliquent des caractères génériques](/windows/desktop/Http/routing-incoming-requests).

Une application exécutée peut créer une demande similaire pour ajouter des inscriptions d'espace de noms. Les inscriptions et les réservations rivalisent pour les parties de l'espace de noms. Une réservation peut avoir priorité sur une inscription en fonction de l’ordre de résolution indiqué dans l' [ordre de résolution entre les revendications d’espace de noms qui impliquent des caractères génériques](/windows/desktop/Http/routing-incoming-requests). Dans ce cas, la réservation empêche à l'application courante de recevoir des demandes.

L’exemple suivant utilise l’outil Netsh.exe :

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

Cette commande ajoute une réservation d’URL pour l’espace de noms d’URL spécifié pour le compte domaine\utilisateur. Pour plus d’informations sur l’utilisation de la commande netsh, tapez `netsh http add urlacl /?` une invite de commandes et appuyez sur entrée.

## <a name="configuring-a-firewall-exception"></a>Configuration d’une exception de pare-feu

Lors de l'auto-hébergement d'un service WCF qui communique sur HTTP, une exception doit être ajoutée à la configuration du pare-feu pour autoriser les connexions entrantes à l'aide d'une URL particulière.

## <a name="configuring-ssl-certificates"></a>Configuration des certificats SSL

Le protocole SSL (Secure Sockets Layer) utilise des certificats sur le client et le serveur pour stocker les clés de chiffrement. Le serveur fournit son certificat SSL à l'établissement d'une connexion afin que le client puisse vérifier son identité. Le serveur peut également demander un certificat au client pour permettre une authentification mutuelle des deux sens de connexion.

Les certificats sont stockés dans un magasin centralisé en fonction de l'adresse IP et du numéro de port de la connexion. L'adresse IP 0.0.0.0 spéciale correspond à l'adresse IP de l'ordinateur local. Notez que le magasin de certificats ne distingue pas les URL en fonction du chemin d’accès. Les services ayant la même combinaison d'adresse IP et de port doivent partager les mêmes certificats même si le chemin d'accès des services dans l'URL est différent.

Pour obtenir des instructions pas à pas, consultez [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>Configuration de la liste d'écoutes IP

L'API du serveur HTTP crée une liaison uniquement avec une adresse IP et un port lorsqu'un utilisateur inscrit une URL. Par défaut, l'API du serveur HTTP crée une liaison avec le port dans l'URL pour toutes les adresses IP de l'ordinateur. Un conflit survient si une application qui n’utilise pas l’API du serveur HTTP a déjà été liée à cette combinaison d’adresse IP et de port. La liste d’écoutes IP permet aux services WCF de coexister avec les applications qui utilisent un port pour certaines des adresses IP de l’ordinateur. Si la liste d'écoutes IP contient une entrée, l'API du serveur HTTP crée seulement une liaison avec les adresses IP spécifiées dans la liste. La modification de la liste d'écoutes IP requiert des privilèges d'administrateur.

Utilisez l’outil netsh pour modifier la liste d’écoute IP, comme illustré dans l’exemple suivant :

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Autres paramètres de configuration

Lors de l'utilisation de <xref:System.ServiceModel.WSDualHttpBinding>, la connexion cliente utilise des valeurs par défaut qui sont compatibles avec les réservations d'espace de noms et le pare-feu de Windows. Si vous choisissez de personnaliser l'adresse cliente de base d'une connexion double, vous devez également configurer ces paramètres HTTP sur le client pour qu'ils correspondent à la nouvelle adresse.

L’API du serveur HTTP contient des paramètres de configuration avancés qui ne sont pas disponibles via HttpCfg. Ces paramètres sont maintenus dans le registre et s'appliquent à toutes les applications exécutées sur les systèmes utilisant les API de serveur HTTP. Pour plus d’informations sur ces paramètres, consultez [Http.sys paramètres de Registre pour IIS](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows). La plupart des utilisateurs n’ont pas besoin de modifier ces paramètres.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Comment : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
