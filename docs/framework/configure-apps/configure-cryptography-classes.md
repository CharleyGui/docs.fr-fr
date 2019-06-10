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
ms.openlocfilehash: b5c1178519601d7dcb7c5b3014f413b6436746fb
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816163"
---
# <a name="configuring-cryptography-classes"></a>Configuration de classes de chiffrement
Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permet aux administrateurs informatiques configurer les algorithmes de chiffrement par défaut et les implémentations d’algorithmes utilisant le .NET Framework et les applications écrites de façon adéquate.  Par exemple, une entreprise qui a sa propre implémentation d’un algorithme de chiffrement possibles que la valeur par défaut au lieu de la mise en œuvre expédié l’implémentation dans le SDK Windows. Applications gérées qui utilisent la cryptographie peuvent toujours choisir de lier de manière explicite à une implémentation particulière, il est recommandé qu’ils créent un objet de chiffrement en utilisant le système de configuration du chiffrement.  
  
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
