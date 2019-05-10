---
title: Modèle de chiffrement de .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42e5c7018f83f3849f46f33e09e09ea1749e7c70
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753288"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="f09eb-102">Modèle de chiffrement de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f09eb-102">.NET Framework Cryptography Model</span></span>

<span data-ttu-id="f09eb-103">.NET Framework fournit des implémentations de nombreux algorithmes de chiffrement standard.</span><span class="sxs-lookup"><span data-stu-id="f09eb-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="f09eb-104">Ces algorithmes sont faciles à utiliser et leurs propriétés par défaut sont les plus sûres possible.</span><span class="sxs-lookup"><span data-stu-id="f09eb-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="f09eb-105">En outre, le modèle de chiffrement .NET Framework de l'héritage d'objets, de la conception orientée flux et de la configuration, est très extensible.</span><span class="sxs-lookup"><span data-stu-id="f09eb-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="f09eb-106">Héritage d'objets</span><span class="sxs-lookup"><span data-stu-id="f09eb-106">Object Inheritance</span></span>

<span data-ttu-id="f09eb-107">Le système de sécurité .NET Framework implémente un modèle extensible d’héritage de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="f09eb-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="f09eb-108">Cette hiérarchie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="f09eb-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="f09eb-109">Classe de type algorithme, telle que <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f09eb-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="f09eb-110">Ce niveau est abstrait.</span><span class="sxs-lookup"><span data-stu-id="f09eb-110">This level is abstract.</span></span>

- <span data-ttu-id="f09eb-111">Classe d'algorithme qui hérite d'une classe de type algorithme, par exemple, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2> ou <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="f09eb-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="f09eb-112">Ce niveau est abstrait.</span><span class="sxs-lookup"><span data-stu-id="f09eb-112">This level is abstract.</span></span>

- <span data-ttu-id="f09eb-113">Implémentation d'une classe d'algorithme qui hérite d'une classe d'algorithme, par exemple, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider> ou <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="f09eb-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="f09eb-114">Ce niveau est totalement implémenté.</span><span class="sxs-lookup"><span data-stu-id="f09eb-114">This level is fully implemented.</span></span>

<span data-ttu-id="f09eb-115">À l’aide de ce modèle de classes dérivées, il est facile d’ajouter un nouvel algorithme ou la nouvelle implémentation d’un algorithme existant.</span><span class="sxs-lookup"><span data-stu-id="f09eb-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="f09eb-116">Par exemple, pour créer un algorithme de clé publique, vous devez hériter de la classe <xref:System.Security.Cryptography.AsymmetricAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f09eb-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="f09eb-117">Pour créer une nouvelle implémentation d'un algorithme spécifique, vous devez créer une classe non abstraite dérivée de cet algorithme.</span><span class="sxs-lookup"><span data-stu-id="f09eb-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="f09eb-118">Comment les algorithmes sont implémentés dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f09eb-118">How Algorithms Are Implemented in the .NET Framework</span></span>

<span data-ttu-id="f09eb-119">Prenez comme exemple d'implémentation les algorithmes symétriques.</span><span class="sxs-lookup"><span data-stu-id="f09eb-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="f09eb-120">La base de tous les algorithmes symétriques est <xref:System.Security.Cryptography.SymmetricAlgorithm>, qui est hérité par les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="f09eb-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>

1. <xref:System.Security.Cryptography.Aes>

2. <xref:System.Security.Cryptography.DES>

3. <xref:System.Security.Cryptography.RC2>

4. <xref:System.Security.Cryptography.Rijndael>

5. <xref:System.Security.Cryptography.TripleDES>

<span data-ttu-id="f09eb-121"><xref:System.Security.Cryptography.Aes> est hérité par deux classes : <xref:System.Security.Cryptography.AesCryptoServiceProvider> et <xref:System.Security.Cryptography.AesManaged>.</span><span class="sxs-lookup"><span data-stu-id="f09eb-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="f09eb-122">La classe <xref:System.Security.Cryptography.AesCryptoServiceProvider> est un wrapper pour l'implémentation de l'API de chiffrement Windows (CAPI) d'AES. La classe <xref:System.Security.Cryptography.AesManaged> est écrite entièrement en code managé.</span><span class="sxs-lookup"><span data-stu-id="f09eb-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="f09eb-123">Il existe également l'implémentation Cryptography Next Generation (CNG), en plus des implémentations CAPI et managées.</span><span class="sxs-lookup"><span data-stu-id="f09eb-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="f09eb-124"><xref:System.Security.Cryptography.ECDiffieHellmanCng> est un exemple d'algorithme CNG.</span><span class="sxs-lookup"><span data-stu-id="f09eb-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="f09eb-125">Les algorithmes CNG sont disponibles sur Windows Vista et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f09eb-125">CNG algorithms are available on Windows Vista and later.</span></span>

<span data-ttu-id="f09eb-126">Vous pouvez choisir l'implémentation qui vous convient le mieux.</span><span class="sxs-lookup"><span data-stu-id="f09eb-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="f09eb-127">Les implémentations managées sont disponibles sur toutes les plateformes qui prennent en charge .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f09eb-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="f09eb-128">Les implémentations CAPI sont disponibles sur les anciens systèmes d'exploitation et ne sont plus développées.</span><span class="sxs-lookup"><span data-stu-id="f09eb-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="f09eb-129">L'implémentation CNG est la plus récente et c'est elle qui fait l'objet des derniers développements en date.</span><span class="sxs-lookup"><span data-stu-id="f09eb-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="f09eb-130">Toutefois, les implémentations managées ne sont pas certifiées par les normes FIPS et peuvent être plus lentes que les classes wrapper.</span><span class="sxs-lookup"><span data-stu-id="f09eb-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>

## <a name="stream-design"></a><span data-ttu-id="f09eb-131">Conception orientée flux</span><span class="sxs-lookup"><span data-stu-id="f09eb-131">Stream Design</span></span>

<span data-ttu-id="f09eb-132">Le Common Language Runtime utilise une conception orientée flux pour implémenter les algorithmes symétriques et les algorithmes de hachage.</span><span class="sxs-lookup"><span data-stu-id="f09eb-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="f09eb-133">La base de cette conception est la classe <xref:System.Security.Cryptography.CryptoStream> qui dérive de la classe <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="f09eb-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="f09eb-134">Les objets de chiffrement basés sur les flux prennent en charge une seule interface standard (`CryptoStream`) pour la gestion du transfert des données de l'objet.</span><span class="sxs-lookup"><span data-stu-id="f09eb-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="f09eb-135">Comme tous les objets sont créés à l'aide d'une interface standard, vous pouvez chaîner plusieurs objets (par exemple, un objet de hachage suivi d'un objet de chiffrement), ainsi qu'effectuer plusieurs opérations sur les données sans avoir besoin de stockage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="f09eb-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="f09eb-136">Le modèle basé sur les flux vous permet également de créer des objets à partir d'objets plus petits.</span><span class="sxs-lookup"><span data-stu-id="f09eb-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="f09eb-137">Par exemple, un algorithme combinant hachage et chiffrement peut être affiché comme un objet de flux unique, même si cet objet a été créé à partir d'un ensemble d'objets de flux.</span><span class="sxs-lookup"><span data-stu-id="f09eb-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>

## <a name="cryptographic-configuration"></a><span data-ttu-id="f09eb-138">Configuration du chiffrement</span><span class="sxs-lookup"><span data-stu-id="f09eb-138">Cryptographic Configuration</span></span>

<span data-ttu-id="f09eb-139">La configuration du chiffrement vous permet de résoudre une implémentation d'un algorithme en un nom d'algorithme. De cette façon, les classes de chiffrement .NET Framework peuvent être étendues.</span><span class="sxs-lookup"><span data-stu-id="f09eb-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="f09eb-140">Vous pouvez ajouter votre propre implémentation logicielle ou matérielle d'un algorithme, puis la mapper vers le nom d'algorithme de votre choix.</span><span class="sxs-lookup"><span data-stu-id="f09eb-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="f09eb-141">Si un algorithme n'est pas spécifié dans le fichier de configuration, les paramètres par défaut sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="f09eb-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="f09eb-142">Pour plus d’informations sur la configuration du chiffrement, consultez [configuration des Classes de chiffrement](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span><span class="sxs-lookup"><span data-stu-id="f09eb-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="f09eb-143">Choix d'un algorithme</span><span class="sxs-lookup"><span data-stu-id="f09eb-143">Choosing an Algorithm</span></span>

<span data-ttu-id="f09eb-144">Vous pouvez sélectionner un algorithme pour différentes raisons. Par exemple, pour l'intégrité ou la confidentialité des données, ou pour générer une clé.</span><span class="sxs-lookup"><span data-stu-id="f09eb-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="f09eb-145">Les algorithmes symétriques et les algorithmes de hachage sont conçus pour protéger les données pour des raisons d'intégrité (empêcher leur modification) ou pour des raisons de confidentialité (empêcher leur affichage).</span><span class="sxs-lookup"><span data-stu-id="f09eb-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="f09eb-146">Les algorithmes de hachage sont principalement utilisés pour l'intégrité des données.</span><span class="sxs-lookup"><span data-stu-id="f09eb-146">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="f09eb-147">Voici une liste des algorithmes recommandés pour chaque application :</span><span class="sxs-lookup"><span data-stu-id="f09eb-147">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="f09eb-148">Confidentialité des données :</span><span class="sxs-lookup"><span data-stu-id="f09eb-148">Data privacy:</span></span>

  - <xref:System.Security.Cryptography.Aes>

- <span data-ttu-id="f09eb-149">Intégrité des données :</span><span class="sxs-lookup"><span data-stu-id="f09eb-149">Data integrity:</span></span>

  - <xref:System.Security.Cryptography.HMACSHA256>

  - <xref:System.Security.Cryptography.HMACSHA512>

- <span data-ttu-id="f09eb-150">Signature numérique :</span><span class="sxs-lookup"><span data-stu-id="f09eb-150">Digital signature:</span></span>

  - <xref:System.Security.Cryptography.ECDsa>

  - <xref:System.Security.Cryptography.RSA>

- <span data-ttu-id="f09eb-151">Échange de clés :</span><span class="sxs-lookup"><span data-stu-id="f09eb-151">Key exchange:</span></span>

  - <xref:System.Security.Cryptography.ECDiffieHellman>

  - <xref:System.Security.Cryptography.RSA>

- <span data-ttu-id="f09eb-152">Génération de nombres aléatoires :</span><span class="sxs-lookup"><span data-stu-id="f09eb-152">Random number generation:</span></span>

  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>

- <span data-ttu-id="f09eb-153">Génération d'une clé à partir d'un mot de passe :</span><span class="sxs-lookup"><span data-stu-id="f09eb-153">Generating a key from a password:</span></span>

  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="f09eb-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f09eb-154">See also</span></span>

- [<span data-ttu-id="f09eb-155">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="f09eb-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
