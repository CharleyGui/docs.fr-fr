---
title: "Service : Nombre d'échecs de validation de la sécurité et d'authentification par seconde"
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 2caebed85a28004ef038beee7d07c05a23da53c0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613679"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>Service : Nombre d'échecs de validation de la sécurité et d'authentification par seconde
Nom du compteur : Validation de la sécurité et les échecs d’authentification par seconde.  
  
## <a name="description"></a>Description  
 Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ». Ces problèmes sont les suivants :  
  
- Impossibilité de lire le jeton client depuis le message.  
  
- Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).  
  
- Échec de la vérification de signature (par exemple, falsification du message).  
  
- Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.  
  
- Impossibilité de déchiffrer le message.  
  
- Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).  
  
- Erreurs lors de la négociation TLSNEGO/SPNEGO.  
  
 Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante,  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
