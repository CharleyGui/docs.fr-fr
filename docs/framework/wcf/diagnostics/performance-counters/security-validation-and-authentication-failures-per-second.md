---
title: Nombre d'échecs de validation de la sécurité et d'authentification par seconde
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 7d680e9a5b03943fdec212c509b6d80a2d60246c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559133"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>Nombre d'échecs de validation de la sécurité et d'authentification par seconde
Nom du compteur : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde.  
  
## <a name="description"></a>Description  
 Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ». Ces problèmes sont les suivants :  
  
- Impossibilité de lire le jeton client depuis le message.  
  
- Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).  
  
- Échec de la vérification de signature (par exemple, falsification du message).  
  
- Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.  
  
- Impossibilité de déchiffrer le message.  
  
- Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).  
  
- Erreurs lors de la négociation TLSNEGO/SPNEGO.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante :  
  
 (N1-N0)/((D1-D0)/F)
