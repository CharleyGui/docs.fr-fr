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
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="bbf00-103">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="bbf00-103">Configuring Cryptography Classes</span></span>
<span data-ttu-id="bbf00-104">Le SDK Windows permet aux administrateurs de l’ordinateur de configurer les algorithmes de chiffrement par défaut et les implémentations d’algorithme que le .NET Framework et les applications écrites de manière appropriée utilisent.</span><span class="sxs-lookup"><span data-stu-id="bbf00-104">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="bbf00-105">Par exemple, une entreprise qui a sa propre implémentation d’un algorithme de chiffrement peut faire de cette implémentation la valeur par défaut au lieu de l’implémentation fournie dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="bbf00-105">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="bbf00-106">Bien que les applications managées qui utilisent le chiffrement puissent toujours choisir de se lier explicitement à une implémentation particulière, il est recommandé de créer des objets de chiffrement à l’aide du système de configuration de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="bbf00-106">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbf00-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bbf00-107">In This Section</span></span>  
 [<span data-ttu-id="bbf00-108">Mappage de noms d'algorithmes à des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="bbf00-108">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="bbf00-109">Décrit comment mapper un nom d’algorithme à une classe de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="bbf00-109">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="bbf00-110">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="bbf00-110">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="bbf00-111">Décrit comment mapper un identificateur d’objet à un algorithme de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="bbf00-111">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bbf00-112">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="bbf00-112">Related Sections</span></span>  
 [<span data-ttu-id="bbf00-113">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="bbf00-113">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="bbf00-114">Fournit une vue d’ensemble des services de chiffrement fournis par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="bbf00-114">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="bbf00-115">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="bbf00-115">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="bbf00-116">Décrit des éléments qui mappent des noms d'algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="bbf00-116">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
