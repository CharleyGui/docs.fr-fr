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
ms.openlocfilehash: e53f4c5c9e24fb25b43b7f27b80ab984214eeac2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927771"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="60a87-102">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="60a87-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="60a87-103">Le SDK Windows permet aux administrateurs de l’ordinateur de configurer les algorithmes de chiffrement par défaut et les implémentations d’algorithme que le .NET Framework et les applications écrites de manière appropriée utilisent.</span><span class="sxs-lookup"><span data-stu-id="60a87-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="60a87-104">Par exemple, une entreprise qui a sa propre implémentation d’un algorithme de chiffrement peut faire de cette implémentation la valeur par défaut au lieu de l’implémentation fournie dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="60a87-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="60a87-105">Bien que les applications managées qui utilisent le chiffrement puissent toujours choisir de se lier explicitement à une implémentation particulière, il est recommandé de créer des objets de chiffrement à l’aide du système de configuration de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="60a87-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60a87-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="60a87-106">In This Section</span></span>  
 [<span data-ttu-id="60a87-107">Mappage de noms d'algorithmes à des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="60a87-107">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="60a87-108">Décrit comment mapper un nom d’algorithme à une classe de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="60a87-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="60a87-109">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="60a87-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="60a87-110">Décrit comment mapper un identificateur d’objet à un algorithme de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="60a87-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="60a87-111">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="60a87-111">Related Sections</span></span>  
 [<span data-ttu-id="60a87-112">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="60a87-112">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="60a87-113">Fournit une vue d’ensemble des services de chiffrement fournis par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="60a87-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="60a87-114">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="60a87-114">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="60a87-115">Décrit des éléments qui mappent des noms d'algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="60a87-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
