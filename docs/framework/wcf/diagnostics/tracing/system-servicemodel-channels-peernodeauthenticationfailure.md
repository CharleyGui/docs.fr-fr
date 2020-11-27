---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: d8abfe6e34439ccf399e37c1285b7b71cebf9870
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258034"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure

Une négociation de sécurité avec un voisin potentiel n'a pas réussi.  
  
## <a name="description"></a>Description  

 Cette trace se produit lors de la tentative d'établissement d'une connexion de voisin sécurisée. Cela peut arriver lorsque les informations d'identification sont incomplètes ou incorrectes.  
  
 PeerChannel reconnaît un seul type de jeton pour les certificats d'identification X.509 puissants qui fournissent un modèle d'identité performant basé sur le type d'authentification et d'autorisation qui peut être implémenté. PeerChannel prend également en charge les applications simples via l'utilisation de mots de passe. Les mots de passe peuvent uniquement être utilisés pour autoriser l'entrée à la session, mais ne peuvent pas l'être pour effectuer l'authentification des messages. Cela et dû au fait qu'un jeton symétrique partagé par un groupe d'homologues est difficile à utiliser et s'avère inapproprié pour l'authentification de la source.  
  
## <a name="troubleshooting"></a>Dépannage  

 Vérifiez que tous les voisins ont les informations d'identification de sécurité appropriées.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité de canal homologue](../../feature-details/peer-channel-security.md)
- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
