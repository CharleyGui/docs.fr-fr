---
title: Configuration de classes de chiffrement
description: Découvrez comment les administrateurs de l’ordinateur peuvent configurer les algorithmes de chiffrement et les implémentations d’algorithme par défaut utilisés par .NET et les applications.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 5d12aae31ec78f80bea7df1bb0f37ac78dc37de2
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105060"
---
# <a name="configuring-cryptography-classes"></a>Configuration de classes de chiffrement
Le SDK Windows permet aux administrateurs de l’ordinateur de configurer les algorithmes de chiffrement par défaut et les implémentations d’algorithme que le .NET Framework et les applications écrites de manière appropriée utilisent.  Par exemple, une entreprise qui a sa propre implémentation d’un algorithme de chiffrement peut faire de cette implémentation la valeur par défaut au lieu de l’implémentation fournie dans le SDK Windows. Bien que les applications managées qui utilisent le chiffrement puissent toujours choisir de se lier explicitement à une implémentation particulière, il est recommandé de créer des objets de chiffrement à l’aide du système de configuration de chiffrement.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappage de noms d'algorithmes à des classes de chiffrement](map-algorithm-names-to-cryptography-classes.md)  
 Décrit comment mapper un nom d’algorithme à une classe de chiffrement.  
  
 [Mappage d'identificateurs d'objet à des algorithmes de chiffrement](map-object-identifiers-to-cryptography-algorithms.md)  
 Décrit comment mapper un identificateur d’objet à un algorithme de chiffrement.  
  
## <a name="related-sections"></a>Sections connexes  
 [Services de chiffrement](../../standard/security/cryptographic-services.md)  
 Fournit une vue d’ensemble des services de chiffrement fournis par le SDK Windows.  
  
 [Schéma des paramètres de chiffrement](./file-schema/cryptography/index.md)  
 Décrit des éléments qui mappent des noms d'algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.
