---
title: Configuration de classes de chiffrement
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567334"
---
# <a name="configuring-cryptography-classes"></a>Configuration de classes de chiffrement
Le SDK Windows permet aux administrateurs de l’ordinateur de configurer les algorithmes de chiffrement par défaut et les implémentations d’algorithme que le .NET Framework et les applications écrites de manière appropriée utilisent.  Par exemple, une entreprise qui a sa propre implémentation d’un algorithme de chiffrement peut faire de cette implémentation la valeur par défaut au lieu de l’implémentation fournie dans le SDK Windows. Bien que les applications managées qui utilisent le chiffrement puissent toujours choisir de se lier explicitement à une implémentation particulière, il est recommandé de créer des objets de chiffrement à l’aide du système de configuration de chiffrement.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappage de noms d'algorithmes à des classes de chiffrement](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Décrit comment mapper un nom d’algorithme à une classe de chiffrement.  
  
 [Mappage d'identificateurs d'objet à des algorithmes de chiffrement](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Décrit comment mapper un identificateur d’objet à un algorithme de chiffrement.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)  
 Fournit une vue d’ensemble des services de chiffrement fournis par le SDK Windows.  
  
 [Schéma des paramètres de chiffrement](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Décrit des éléments qui mappent des noms d'algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.
