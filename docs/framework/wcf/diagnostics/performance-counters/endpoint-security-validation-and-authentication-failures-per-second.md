---
title: 'Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: fb882c7cbfd86e1949798df9c0b7514182c1b8f6
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163525"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde
Nom du compteur : Nombre d’échecs de validation de la sécurité et d’authentification par seconde  
  
## <a name="description"></a>Description  
 Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ». Ces problèmes sont les suivants :  
  
- Impossibilité de lire le jeton client depuis le message.  
  
- Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).  
  
- Échec de la vérification de signature (par exemple, falsification du message).  
  
- Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.  
  
- Impossibilité de déchiffrer le message.  
  
- Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).  
  
- Erreurs lors de la négociation TLSNEGO/SPNEGO.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante :  
  
 (N1-N0)/((D1-D0)/F)
