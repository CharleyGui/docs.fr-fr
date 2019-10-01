---
title: Élément <cryptoNameMapping>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: 45d2da22a7c3486d4c7a638e92d1f3fce6f9883c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699715"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="06a5a-102">Élément @no__t 0cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="06a5a-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="06a5a-103">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="06a5a-103">Contains mappings of classes to friendly names.</span></span>  
  
[<span data-ttu-id="06a5a-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="06a5a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="06a5a-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="06a5a-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="06a5a-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="06a5a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="06a5a-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="06a5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06a5a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06a5a-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06a5a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="06a5a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="06a5a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="06a5a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06a5a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="06a5a-111">Attributes</span></span>  
 <span data-ttu-id="06a5a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="06a5a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06a5a-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="06a5a-113">Child Elements</span></span>  
  
|<span data-ttu-id="06a5a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="06a5a-114">Element</span></span>|<span data-ttu-id="06a5a-115">Description</span><span class="sxs-lookup"><span data-stu-id="06a5a-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="06a5a-116">Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="06a5a-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="06a5a-117">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="06a5a-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06a5a-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="06a5a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="06a5a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="06a5a-119">Element</span></span>|<span data-ttu-id="06a5a-120">Description</span><span class="sxs-lookup"><span data-stu-id="06a5a-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="06a5a-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06a5a-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="06a5a-122">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="06a5a-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="06a5a-123">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="06a5a-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="06a5a-124">Contient l’élément > @no__t 0cryptographySettings.</span><span class="sxs-lookup"><span data-stu-id="06a5a-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06a5a-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="06a5a-125">Example</span></span>  
 <span data-ttu-id="06a5a-126">L’exemple suivant montre comment utiliser l’élément **\<cryptoNameMapping >** pour faire référence à une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="06a5a-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="06a5a-127">Vous pouvez ensuite passer la chaîne « RSA » à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="06a5a-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06a5a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06a5a-128">See also</span></span>

- [<span data-ttu-id="06a5a-129">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="06a5a-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="06a5a-130">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="06a5a-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="06a5a-131">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="06a5a-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="06a5a-132">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="06a5a-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
