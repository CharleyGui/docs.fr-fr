---
title: Modèle de chiffrement .NET
description: Passez en revue les implémentations des algorithmes de chiffrement habituels dans .NET. Découvrez le modèle de chiffrement extensible de l’héritage d’objets, de la conception de flux & de la configuration.
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: f9ec08992cb8db8f81f11de661612e1b7d15131c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831115"
---
# <a name="net-cryptography-model"></a><span data-ttu-id="09fd5-104">Modèle de chiffrement .NET</span><span class="sxs-lookup"><span data-stu-id="09fd5-104">.NET Cryptography Model</span></span>

<span data-ttu-id="09fd5-105">.NET fournit des implémentations de nombreux algorithmes de chiffrement standard, et le modèle de chiffrement .NET est extensible.</span><span class="sxs-lookup"><span data-stu-id="09fd5-105">.NET provides implementations of many standard cryptographic algorithms, and the .NET cryptography model is extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="09fd5-106">Héritage d'objet</span><span class="sxs-lookup"><span data-stu-id="09fd5-106">Object Inheritance</span></span>

<span data-ttu-id="09fd5-107">Le système de chiffrement .NET implémente un modèle extensible d’héritage de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="09fd5-107">The .NET cryptography system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="09fd5-108">Cette hiérarchie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="09fd5-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="09fd5-109">Classe de type algorithme, telle que <xref:System.Security.Cryptography.SymmetricAlgorithm> ,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="09fd5-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm>, or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="09fd5-110">Ce niveau est abstrait.</span><span class="sxs-lookup"><span data-stu-id="09fd5-110">This level is abstract.</span></span>

- <span data-ttu-id="09fd5-111">Classe d'algorithme qui hérite d'une classe de type algorithme, par exemple, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA> ou <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="09fd5-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="09fd5-112">Ce niveau est abstrait.</span><span class="sxs-lookup"><span data-stu-id="09fd5-112">This level is abstract.</span></span>

- <span data-ttu-id="09fd5-113">Implémentation d'une classe d'algorithme qui hérite d'une classe d'algorithme, par exemple, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider> ou <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="09fd5-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="09fd5-114">Ce niveau est totalement implémenté.</span><span class="sxs-lookup"><span data-stu-id="09fd5-114">This level is fully implemented.</span></span>

<span data-ttu-id="09fd5-115">Ce modèle de classes dérivées vous permet d’ajouter un nouvel algorithme ou une nouvelle implémentation d’un algorithme existant.</span><span class="sxs-lookup"><span data-stu-id="09fd5-115">This pattern of derived classes lets you add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="09fd5-116">Par exemple, pour créer un algorithme de clé publique, vous devez hériter de la classe <xref:System.Security.Cryptography.AsymmetricAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="09fd5-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="09fd5-117">Pour créer une nouvelle implémentation d'un algorithme spécifique, vous devez créer une classe non abstraite dérivée de cet algorithme.</span><span class="sxs-lookup"><span data-stu-id="09fd5-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-net"></a><span data-ttu-id="09fd5-118">Comment les algorithmes sont implémentés dans .NET</span><span class="sxs-lookup"><span data-stu-id="09fd5-118">How Algorithms Are Implemented in .NET</span></span>

<span data-ttu-id="09fd5-119">Prenez comme exemple d'implémentation les algorithmes symétriques.</span><span class="sxs-lookup"><span data-stu-id="09fd5-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="09fd5-120">La base de tous les algorithmes symétriques est <xref:System.Security.Cryptography.SymmetricAlgorithm> , qui est héritée par <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.TripleDES> et d’autres qui ne sont plus recommandées.</span><span class="sxs-lookup"><span data-stu-id="09fd5-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.TripleDES>, and others that are no longer recommended.</span></span>

<span data-ttu-id="09fd5-121"><xref:System.Security.Cryptography.Aes> est hérité par <xref:System.Security.Cryptography.AesCryptoServiceProvider> , <xref:System.Security.Cryptography.AesCng> et <xref:System.Security.Cryptography.AesManaged> .</span><span class="sxs-lookup"><span data-stu-id="09fd5-121"><xref:System.Security.Cryptography.Aes> is inherited by <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng>, and <xref:System.Security.Cryptography.AesManaged>.</span></span>

<span data-ttu-id="09fd5-122">Dans .NET Framework sur Windows :</span><span class="sxs-lookup"><span data-stu-id="09fd5-122">In .NET Framework on Windows:</span></span>

* <span data-ttu-id="09fd5-123">`*CryptoServiceProvider` les classes d’algorithme, telles que <xref:System.Security.Cryptography.AesCryptoServiceProvider> , sont des wrappers autour de l’implémentation de l’API de chiffrement Windows (CAPI) d’un algorithme.</span><span class="sxs-lookup"><span data-stu-id="09fd5-123">`*CryptoServiceProvider` algorithm classes, such as <xref:System.Security.Cryptography.AesCryptoServiceProvider>, are wrappers around the Windows Cryptography API (CAPI) implementation of an algorithm.</span></span>
* <span data-ttu-id="09fd5-124">`*Cng` les classes d’algorithme, telles que <xref:System.Security.Cryptography.ECDiffieHellmanCng> , sont des wrappers autour de l’implémentation CNG (Windows Cryptography Next Generation).</span><span class="sxs-lookup"><span data-stu-id="09fd5-124">`*Cng` algorithm classes, such as <xref:System.Security.Cryptography.ECDiffieHellmanCng>, are wrappers around the Windows Cryptography Next Generation (CNG) implementation.</span></span>
* <span data-ttu-id="09fd5-125">`*Managed` les classes, telles que <xref:System.Security.Cryptography.AesManaged> , sont écrites entièrement dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="09fd5-125">`*Managed` classes, such as <xref:System.Security.Cryptography.AesManaged>, are written entirely in managed code.</span></span> <span data-ttu-id="09fd5-126">`*Managed` les implémentations ne sont pas certifiées par les normes FIPS (Federal Information Processing Standards) et peuvent être plus lentes que les `*CryptoServiceProvider` `*Cng` classes wrapper et.</span><span class="sxs-lookup"><span data-stu-id="09fd5-126">`*Managed` implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the `*CryptoServiceProvider` and `*Cng` wrapper classes.</span></span>

<span data-ttu-id="09fd5-127">Dans .NET Core et .NET 5 et versions ultérieures, toutes les classes d’implémentation ( `*CryptoServiceProvider` , `*Managed` et `*Cng` ) sont des wrappers pour les algorithmes du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="09fd5-127">In .NET Core and .NET 5 and later versions, all implementation classes (`*CryptoServiceProvider`, `*Managed`, and `*Cng`) are wrappers for the operating system (OS) algorithms.</span></span> <span data-ttu-id="09fd5-128">Si les algorithmes de système d’exploitation sont certifiés FIPS, .NET utilise des algorithmes certifiés FIPS.</span><span class="sxs-lookup"><span data-stu-id="09fd5-128">If the OS algorithms are FIPS-certified, then .NET uses FIPS-certified algorithms.</span></span> <span data-ttu-id="09fd5-129">Pour plus d’informations, consultez la page [chiffrement multiplateforme](cross-platform-cryptography.md).</span><span class="sxs-lookup"><span data-stu-id="09fd5-129">For more information, see [Cross-Platform Cryptography](cross-platform-cryptography.md).</span></span>

<span data-ttu-id="09fd5-130">Dans la plupart des cas, vous n’avez pas besoin de référencer directement une classe d’implémentation d’algorithme, telle que `AesCryptoServiceProvider` .</span><span class="sxs-lookup"><span data-stu-id="09fd5-130">In most cases, you don't need to directly reference an algorithm implementation class, such as `AesCryptoServiceProvider`.</span></span> <span data-ttu-id="09fd5-131">Les méthodes et les propriétés dont vous avez généralement besoin sont sur la classe d’algorithme de base, par exemple `Aes` .</span><span class="sxs-lookup"><span data-stu-id="09fd5-131">The methods and properties you typically need are on the base algorithm class, such as `Aes`.</span></span> <span data-ttu-id="09fd5-132">Créez une instance d’une classe d’implémentation par défaut en utilisant une méthode de fabrique sur la classe d’algorithme de base et reportez-vous à la classe d’algorithme de base.</span><span class="sxs-lookup"><span data-stu-id="09fd5-132">Create an instance of a default implementation class by using a factory method on the base algorithm class, and refer to the base algorithm class.</span></span> <span data-ttu-id="09fd5-133">Par exemple, consultez la ligne de code en surbrillance dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="09fd5-133">For example, see the highlighted line of code in the following example:</span></span>

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="16":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="12":::

## <a name="cryptographic-configuration"></a><span data-ttu-id="09fd5-134">Configuration du chiffrement</span><span class="sxs-lookup"><span data-stu-id="09fd5-134">Cryptographic Configuration</span></span>

<span data-ttu-id="09fd5-135">La configuration du chiffrement vous permet de résoudre une implémentation spécifique d’un algorithme en un nom d’algorithme, ce qui permet l’extensibilité des classes de chiffrement .NET.</span><span class="sxs-lookup"><span data-stu-id="09fd5-135">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET cryptography classes.</span></span> <span data-ttu-id="09fd5-136">Vous pouvez ajouter votre propre implémentation logicielle ou matérielle d'un algorithme, puis la mapper vers le nom d'algorithme de votre choix.</span><span class="sxs-lookup"><span data-stu-id="09fd5-136">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="09fd5-137">Si un algorithme n'est pas spécifié dans le fichier de configuration, les paramètres par défaut sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="09fd5-137">If an algorithm is not specified in the configuration file, the default settings are used.</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="09fd5-138">Choix d'un algorithme</span><span class="sxs-lookup"><span data-stu-id="09fd5-138">Choosing an Algorithm</span></span>

<span data-ttu-id="09fd5-139">Vous pouvez sélectionner un algorithme pour différentes raisons. Par exemple, pour l'intégrité ou la confidentialité des données, ou pour générer une clé.</span><span class="sxs-lookup"><span data-stu-id="09fd5-139">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="09fd5-140">Les algorithmes symétriques et les algorithmes de hachage sont conçus pour protéger les données pour des raisons d'intégrité (empêcher leur modification) ou pour des raisons de confidentialité (empêcher leur affichage).</span><span class="sxs-lookup"><span data-stu-id="09fd5-140">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="09fd5-141">Les algorithmes de hachage sont principalement utilisés pour l'intégrité des données.</span><span class="sxs-lookup"><span data-stu-id="09fd5-141">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="09fd5-142">Voici une liste des algorithmes recommandés pour chaque application :</span><span class="sxs-lookup"><span data-stu-id="09fd5-142">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="09fd5-143">Confidentialité des données :</span><span class="sxs-lookup"><span data-stu-id="09fd5-143">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="09fd5-144">Intégrité des données :</span><span class="sxs-lookup"><span data-stu-id="09fd5-144">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="09fd5-145">Signature numérique :</span><span class="sxs-lookup"><span data-stu-id="09fd5-145">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="09fd5-146">Échange de clés :</span><span class="sxs-lookup"><span data-stu-id="09fd5-146">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="09fd5-147">Génération de nombres aléatoires :</span><span class="sxs-lookup"><span data-stu-id="09fd5-147">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- <span data-ttu-id="09fd5-148">Génération d'une clé à partir d'un mot de passe :</span><span class="sxs-lookup"><span data-stu-id="09fd5-148">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="09fd5-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09fd5-149">See also</span></span>

- [<span data-ttu-id="09fd5-150">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="09fd5-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="09fd5-151">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="09fd5-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="09fd5-152">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="09fd5-152">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
