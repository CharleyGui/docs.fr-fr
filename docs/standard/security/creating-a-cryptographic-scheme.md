---
title: Création d'un modèle de chiffrement
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288418"
---
# <a name="creating-a-cryptographic-scheme"></a>Création d'un modèle de chiffrement
Les composants de chiffrement de .NET Framework peuvent être combinés pour créer différents modèles permettant de chiffrer et de déchiffrer des données.  
  
 Un simple modèle de chiffrement pour chiffrer et déchiffrer des données peut spécifier les étapes suivantes :  
  
1. Chaque partie génère une paire de clés publique/privée.  
  
2. Les parties échangent leurs clés publiques.  
  
3. Chaque partie génère une clé secrète pour le chiffrement TripleDES (par exemple), et chiffre la clé nouvellement créée à l'aide de la clé publique de l'autre.  
  
4. Chaque partie envoie les données à l'autre et combine la clé secrète de l'autre avec la sienne, dans un ordre spécifique, pour créer une clé secrète.  
  
5. Les parties lancent ensuite une conversation à l'aide du chiffrement symétrique.  
  
 La création d’un modèle de chiffrement n’est pas une tâche facile.
  
## <a name="see-also"></a>Voir aussi

- [Services de chiffrement](cryptographic-services.md)
