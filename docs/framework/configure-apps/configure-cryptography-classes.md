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
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="a8e8c-102">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a8e8c-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="a8e8c-103">Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permet aux administrateurs informatiques configurer les algorithmes de chiffrement par défaut et les implémentations d’algorithmes utilisant le .NET Framework et les applications écrites de façon adéquate.</span><span class="sxs-lookup"><span data-stu-id="a8e8c-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="a8e8c-104">Par exemple, une entreprise qui a sa propre implémentation d’un algorithme de chiffrement possibles que la valeur par défaut au lieu de la mise en œuvre expédié l’implémentation dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="a8e8c-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="a8e8c-105">Applications gérées qui utilisent la cryptographie peuvent toujours choisir de lier de manière explicite à une implémentation particulière, il est recommandé qu’ils créent un objet de chiffrement en utilisant le système de configuration du chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a8e8c-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8e8c-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a8e8c-106">In This Section</span></span>  
 [<span data-ttu-id="a8e8c-107">Mappage de noms d'algorithmes à des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a8e8c-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="a8e8c-108">Décrit comment mapper un nom d’algorithme à une classe de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a8e8c-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="a8e8c-109">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a8e8c-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="a8e8c-110">Décrit comment mapper un identificateur d’objet à un algorithme de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a8e8c-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8e8c-111">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a8e8c-111">Related Sections</span></span>  
 [<span data-ttu-id="a8e8c-112">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="a8e8c-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="a8e8c-113">Fournit une vue d’ensemble des services de chiffrement fournis par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="a8e8c-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="a8e8c-114">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a8e8c-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="a8e8c-115">Décrit des éléments qui mappent des noms d'algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a8e8c-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
