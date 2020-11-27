---
title: Interprétation de codes d'erreur retournés par wsatConfig.exe
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: c5f423f5054a3a80bc0c730444ca9e90c203e288
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262747"
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interprétation de codes d'erreur retournés par wsatConfig.exe

Cette rubrique répertorie tous les codes d'erreur générés par l'utilitaire de configuration de WS-AtomicTransaction (wsatConfig.exe), et les actions recommandées.  
  
## <a name="list-of-error-codes"></a>Liste de codes d'erreur  
  
|Code d'erreur|Description|Action recommandée|  
|----------------|-----------------|------------------------------------|  
|0|L’opération a réussi|Aucune|  
|1|Erreur inattendue|Contacter Microsoft|  
|2|Une erreur inattendue s'est produite lors de la tentative de contact de MSDTC pour récupérer les paramètres de sécurité.|Vérifiez que le service MSDTC n'est pas désactivé et traitez tous les problèmes répertoriés dans l'exception retournée.|  
|3|Le compte via lequel WsatConfig.exe a été exécuté ne disposait pas des autorisations suffisantes pour lire les paramètres de sécurité du réseau.|Exécutez WsatConfig.exe en utilisant un compte d'administrateur.|  
|4|Activez l'option d'accès DTC réseau pour MSDTC avant d'essayer d'activer le support WS-AT.|Activez l'option d'accès DTC réseau pour MSDTC et ré-exécutez l'utilitaire.|  
|5|Le port entré était hors limites. La valeur doit être comprise entre 1 et 65535|Corrigez l'option de ligne de commande `-port:<portNum>`<br /><br /> selon les indications du message d'erreur.|  
|6|Un certificat de point de terminaison incorrect a été spécifié sur la ligne de commande.  Ce certificat est introuvable ou sa vérification a échoué.|Corrigez l'option de ligne de commande `-endpointCert`. Vérifiez que le certificat a une clé privée, qu'il doit être utilisé pour ClientAuthentication et ServerAuthentication, qu'il est installé dans le magasin de certificats LocalMachine\MY et qu'il bénéficie d'un niveau de confiance total.|  
|7|Un certificat de compte incorrect a été spécifié sur la ligne de commande.|Corrigez l'option de ligne de commande `-accountsCerts`. Le certificat a été spécifié de façon incorrecte ou il est introuvable.|  
|8|Un délai d'attente par défaut a été spécifié hors de la plage de 1 à 3600 secondes.|Entrez une valeur de délai d'attente par défaut correcte, selon les indications.|  
|10|Une erreur inattendue s'est produite pendant la tentative d'accès au registre.|Vérifiez le message d'erreur et le code d'erreur pour les éléments sur lesquels une action peut être effectuée.|  
|11|Impossible d'écrire dans le registre.|Vérifiez que la clé répertoriée dans le message d'erreur est capable d'accéder au registre à partir du compte sous lequel WsatConfig.exe a été exécuté.|  
|12|Une erreur inattendue s'est produite lors de la tentative d'accès au magasin de certificats.|Utilisez le code d'erreur retourné pour effecteur un mappage avec l'erreur système appropriée.|  
|13|La configuration d'http.sys a échoué. Impossible de créer une nouvelle réservation de port HTTPS pour MSDTC.|Utilisez le code d'erreur retourné pour effecteur un mappage avec l'erreur système appropriée.|  
|14|La configuration d'http.sys a échoué. Impossible de supprimer la précédente réservation de port HTTPS pour MSDTC.|Utilisez le code d'erreur retourné pour effecteur un mappage avec l'erreur système appropriée.|  
|15|La configuration d'http.sys a échoué. Une réservation de port HTTPS précédente existe déjà pour le port spécifié.|Une autre application s'est déjà approprié le port spécifique. Indiquez un autre port, désinstallez ou reconfigurez l'application actuelle.|  
|16|La configuration d'http.sys a échoué. Impossible de lier le certificat spécifié au port.|Utilisez le code d'erreur retourné dans le message d'erreur pour effecteur un mappage avec l'erreur système appropriée.|  
|17|La configuration d'http.sys a échoué. Impossible d’annuler la liaison du certificat SSL au port précédent.|Utilisez le code d'erreur retourné dans le message d'erreur pour effecteur un mappage avec l'erreur système appropriée. En cas de besoin, utilisez httpcfg.exe ou netsh.exe pour supprimer les réservations de port erronées.|  
|18|La configuration d'http.sys a échoué. Impossible de lier le certificat spécifié au port, car une liaison SSL précédente existe déjà.|Une autre application s'est déjà approprié le port spécifique. Indiquez un autre port, désinstallez ou reconfigurez l'application actuelle.|  
|19|Le redémarrage de MSDTC a échoué|Redémarrez manuellement MSDTC si nécessaire. Si le problème persiste, contactez Microsoft.|  
|20|WinFX n’est pas installé sur la machine distante ou n’est pas installé correctement.|Installez WinFX sur l’ordinateur.|  
|21|La configuration distante a échoué en raison de l'expiration du délai d'attente.|L'appel de configuration de WS-AT sur l'ordinateur distant doit durer plus de 90 secondes.|  
|22|WinFX n’est pas installé sur la machine distante ou n’est pas installé correctement.|Installez WinFX sur l’ordinateur.|  
|23|La configuration distante a échoué en raison d'une exception sur l'ordinateur distant.|Examinez le message d'erreur pour rechercher les éléments sur lesquels une action peut être effectuée.|  
|26|Un argument incorrect a été passé à WsatConfig.exe.|Recherchez les erreurs sur la ligne de commande.|  
|27|L'option de ligne de commande `-accounts` est incorrecte.|Corrigez l'option de ligne de commande `accounts` pour spécifier un compte d'utilisateur correct.|  
|28|L'option de ligne de commande `-network` est incorrecte.|Corrigez l'option de ligne de commande `-network` en spécifiant correctement "activer" ou "désactiver".|  
|29|L'option de ligne de commande `-maxTimeout` est incorrecte.|Corrigez l'option de ligne de commande `-maxTimeout` selon les indications.|  
|30|L'option de ligne de commande `-timeout` est incorrecte.|Corrigez l'option de ligne de commande `-timeout` selon les indications.|  
|31|L'option de ligne de commande `-traceLevel` est incorrecte.|Corrigez l'option de ligne de commande `-traceLevel` en spécifiant une valeur valide parmi les valeurs suivantes :<br /><br /> -Désactivé<br />-   Error<br />-   Critical<br />- Avertissement<br />-Informations<br />-Verbose<br />-Tout|  
|32|L'option de ligne de commande `-traceActivity` est incorrecte.|Corrigez l'option de ligne de commande `-traceActivity` en spécifiant "activer" ou "désactiver".|  
|33|L'option de ligne de commande `-traceProp` est incorrecte.|Corrigez l'option de ligne de commande `-traceProp` en spécifiant "activer" ou "désactiver".|  
|34|L'option de ligne de commande `-tracePII` est incorrecte.|Corrigez l'option de ligne de commande `-tracePII` en spécifiant "activer" ou "désactiver".|  
|37|WsatConfig.exe n'est pas parvenu à déterminer le certificat d'ordinateur exact. Cela peut se produire lorsqu'il existe plusieurs candidats, ou qu'aucun candidat n'existe.|Spécifiez une empreinte numérique de certificat ou une paire Issuer\SubjectName -correcte pour identifier le certificat exact à configurer.|  
|38|Le processus ou l'utilisateur ne dispose pas des autorisations suffisantes pour modifier la configuration du pare-feu.|Exécutez WsatConfig.exe en utilisant un compte d'administrateur.|  
|39|WsatConfig.exe a rencontré une erreur en mettant à jour la configuration du pare-feu.|Examinez le message d'erreur pour rechercher les éléments sur lesquels une action peut être effectuée.|  
|40|WsatConfig.exe ne parvient pas à fournir l'accès en lecture MSDTC au fichier de clé privée du certificat|Exécutez WsatConfig.exe en utilisant un compte d'administrateur.|  
|41|Soit aucune installation de WinFX n’a été trouvée, soit la version trouvée ne correspond pas à ce que l’outil est capable de configurer.|Vérifiez que WinFX est correctement installé et utilisez uniquement l’outil WsatConfig.exe fourni avec cette version de WinFX pour configurer WS-AT.|  
|42|Un argument a été spécifié plusieurs fois sur la ligne de commande.|Veillez à spécifier chaque argument une seule fois lors de l’exécution de WsatConfig.exe.|  
|43|WsatConfig.exe ne parvient pas à mettre à jour les paramètres WS-AT si WS-AT n'est pas activé.|Spécifiez `-network:enable` en tant qu'argument supplémentaire de ligne de commande.|  
|44|Un correctif logiciel requis est manquant et WS-AT ne peut pas être configuré tant que ce correctif logiciel n'est pas installé.|Consultez les notes de publication de WinFX pour obtenir des instructions sur l’installation du correctif logiciel requis.|  
|45|L'option de ligne de commande `-virtualServer` est incorrecte.|Corrigez l'option de ligne de commande `-virtualServer` en spécifiant le nom de réseau de la ressource de cluster dans lequel la configuration doit s'effectuer.|  
|46|Une erreur inattendue s'est produite lors de la tentative de démarrage de la session de suivi ETW|Utilisez le code d'erreur retourné pour effecteur un mappage avec l'erreur système appropriée.|  
|47|Le processus ou l'utilisateur ne dispose pas des autorisations suffisantes pour activer la session de suivi ETW.|Exécutez WsatConfig.exe en utilisant un compte d'administrateur.|  
|48|Une erreur inattendue s'est produite lors de la tentative de démarrage de la session de suivi ETW|Contactez Microsoft.|  
|49|Impossible de créer un nouveau fichier journal en raison d'une quantité d'espace insuffisante dans %systemdrive%|Vérifiez que % systemdrive% dispose d'une quantité d'espace suffisante pour le fichier journal.|  
|51|Une erreur inattendue s'est produite lors de la tentative de démarrage de la session de suivi ETW|Contactez Microsoft.|  
|52|Une erreur inattendue s'est produite lors de la tentative de démarrage de la session de suivi ETW|Contactez Microsoft.|  
|53|La sauvegarde du fichier journal de la session ETW précédente a échoué.|Vérifiez que % systemdrive% dispose d'une quantité d''espace suffisante pour le fichier journal et pour la sauvegarde du fichier journal précédent (le cas échéant). Supprimez manuellement le fichier journal précédent, en cas de besoin.|  
|55|Une erreur inattendue s'est produite lors de la tentative de démarrage de la session de suivi ETW|Contactez Microsoft.|  
|56|Une erreur inattendue s'est produite lors de la tentative de démarrage de la session de suivi ETW|Contactez Microsoft.|  
  
## <a name="see-also"></a>Voir aussi

- [Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
