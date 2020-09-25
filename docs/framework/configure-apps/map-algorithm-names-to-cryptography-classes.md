---
title: Mappage de noms d'algorithmes à des classes de chiffrement
description: Mappez les noms d’algorithmes à des classes de chiffrement dans .NET. Un développeur a quatre options pour créer un objet de chiffrement.
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: b67db612496e56a341dab2e5fc4b52c954ff02b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183388"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="06c8c-104">Mappage de noms d'algorithmes à des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="06c8c-104">Mapping Algorithm Names to Cryptography Classes</span></span>

<span data-ttu-id="06c8c-105">Un développeur peut créer un objet de chiffrement à l’aide de l’SDK Windows de quatre façons :</span><span class="sxs-lookup"><span data-stu-id="06c8c-105">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="06c8c-106">Créez un objet à l’aide de l’opérateur **New** .</span><span class="sxs-lookup"><span data-stu-id="06c8c-106">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="06c8c-107">Créez un objet qui implémente un algorithme de chiffrement particulier en appelant la méthode **Create** sur la classe abstraite pour cet algorithme.</span><span class="sxs-lookup"><span data-stu-id="06c8c-107">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="06c8c-108">Créez un objet qui implémente un algorithme de chiffrement particulier en appelant la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="06c8c-108">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="06c8c-109">Créez un objet qui implémente une classe d’algorithmes de chiffrement (par exemple, un chiffrement par bloc symétrique) en appelant la méthode **Create** sur la classe abstraite pour ce type d’algorithme (tel que <xref:System.Security.Cryptography.SymmetricAlgorithm> ).</span><span class="sxs-lookup"><span data-stu-id="06c8c-109">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="06c8c-110">Par exemple, supposons qu’un développeur souhaite calculer le hachage SHA1 d’un ensemble d’octets.</span><span class="sxs-lookup"><span data-stu-id="06c8c-110">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="06c8c-111">L' <xref:System.Security.Cryptography> espace de noms contient deux implémentations de l’algorithme SHA1, une implémentation purement managée et une implémentation qui encapsule CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="06c8c-111">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="06c8c-112">Le développeur peut choisir d’instancier une implémentation SHA1 particulière (telle que <xref:System.Security.Cryptography.SHA1Managed> ) en appelant l’opérateur **New** .</span><span class="sxs-lookup"><span data-stu-id="06c8c-112">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="06c8c-113">Toutefois, s’il importe peu la classe que le common language runtime charge, tant que la classe implémente l’algorithme de hachage SHA1, le développeur peut créer un objet en appelant la <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="06c8c-113">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="06c8c-114">Cette méthode appelle **System. Security. Cryptography. CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")**, qui doit retourner une implémentation de l’algorithme de hachage SHA1.</span><span class="sxs-lookup"><span data-stu-id="06c8c-114">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="06c8c-115">Le développeur peut également appeler **System. Security. Cryptography. CryptoConfig. CreateFromName ("SHA1")** car, par défaut, la configuration du chiffrement comprend des noms courts pour les algorithmes fournis dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06c8c-115">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="06c8c-116">Si l’algorithme de hachage utilisé n’a pas d’importance, le développeur peut appeler la <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> méthode, qui retourne un objet qui implémente une transformation de hachage.</span><span class="sxs-lookup"><span data-stu-id="06c8c-116">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="06c8c-117">Mappage des noms d’algorithmes dans les fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="06c8c-117">Mapping Algorithm Names in Configuration Files</span></span>  

 <span data-ttu-id="06c8c-118">Par défaut, le runtime retourne un <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objet pour les quatre scénarios.</span><span class="sxs-lookup"><span data-stu-id="06c8c-118">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="06c8c-119">Toutefois, un administrateur d’ordinateur peut modifier le type d’objet retourné par les méthodes dans les deux derniers scénarios.</span><span class="sxs-lookup"><span data-stu-id="06c8c-119">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="06c8c-120">Pour ce faire, vous devez mapper un nom d’algorithme convivial à la classe que vous souhaitez utiliser dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="06c8c-120">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="06c8c-121">L’exemple suivant montre comment configurer le runtime afin que **System. Security. Cryptography. SHA1. Create**, **System. Security. CryptoConfig. CREATEFROMNAME ("SHA1")** et **System. Security. Cryptography. HashAlgorithm. Create** retournent un `MySHA1HashClass` objet.</span><span class="sxs-lookup"><span data-stu-id="06c8c-121">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="06c8c-122">Vous pouvez spécifier le nom de l’attribut dans l' [ \> élément<cryptoClass](./file-schema/cryptography/cryptoclass-element.md) (l’exemple précédent nomme l’attribut `MySHA1Hash` ).</span><span class="sxs-lookup"><span data-stu-id="06c8c-122">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="06c8c-123">La valeur de l’attribut dans l' **\<cryptoClass>** élément est une chaîne que l’Common Language Runtime utilise pour rechercher la classe.</span><span class="sxs-lookup"><span data-stu-id="06c8c-123">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="06c8c-124">Vous pouvez utiliser n’importe quelle chaîne conforme aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="06c8c-124">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="06c8c-125">De nombreux noms d’algorithmes peuvent être mappés à la même classe.</span><span class="sxs-lookup"><span data-stu-id="06c8c-125">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="06c8c-126">L' [ \<nameEntry> élément](./file-schema/cryptography/nameentry-element.md) mappe une classe à un nom d’algorithme convivial.</span><span class="sxs-lookup"><span data-stu-id="06c8c-126">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="06c8c-127">L’attribut **Name** peut être soit une chaîne utilisée lors de l’appel de la méthode **System. Security. Cryptography. CryptoConfig. CreateFromName** , soit le nom d’une classe de chiffrement abstraite dans l' <xref:System.Security.Cryptography> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="06c8c-127">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="06c8c-128">La valeur de l’attribut de **classe** est le nom de l’attribut dans l' **\<cryptoClass>** élément.</span><span class="sxs-lookup"><span data-stu-id="06c8c-128">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06c8c-129">Vous pouvez récupérer un algorithme SHA1 en appelant la <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> méthode ou la méthode **Security. CryptoConfig. CreateFromName ("SHA1")** .</span><span class="sxs-lookup"><span data-stu-id="06c8c-129">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="06c8c-130">Chaque méthode garantit uniquement qu’elle retourne un objet qui implémente l’algorithme SHA1.</span><span class="sxs-lookup"><span data-stu-id="06c8c-130">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="06c8c-131">Vous n’avez pas besoin de mapper chaque nom convivial d’un algorithme à la même classe dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="06c8c-131">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="06c8c-132">Pour obtenir la liste des noms par défaut et des classes avec lesquelles ils sont mappés, consultez <xref:System.Security.Cryptography.CryptoConfig> .</span><span class="sxs-lookup"><span data-stu-id="06c8c-132">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c8c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06c8c-133">See also</span></span>

- [<span data-ttu-id="06c8c-134">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="06c8c-134">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="06c8c-135">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="06c8c-135">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
