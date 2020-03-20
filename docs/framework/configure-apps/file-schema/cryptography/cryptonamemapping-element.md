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
ms.openlocfilehash: d31c5cd52ffe0e2a6eb5784735e76436d216444b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155217"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="e5186-102">\<cryptoNameMapping> Element</span><span class="sxs-lookup"><span data-stu-id="e5186-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="e5186-103">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="e5186-103">Contains mappings of classes to friendly names.</span></span>  

<span data-ttu-id="e5186-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5186-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e5186-105">&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e5186-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="e5186-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographieSettings>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5186-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="e5186-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="e5186-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e5186-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5186-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5186-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5186-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e5186-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e5186-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5186-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e5186-111">Attributes</span></span>  
 <span data-ttu-id="e5186-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e5186-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5186-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5186-113">Child Elements</span></span>  
  
|<span data-ttu-id="e5186-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e5186-114">Element</span></span>|<span data-ttu-id="e5186-115">Description</span><span class="sxs-lookup"><span data-stu-id="e5186-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="e5186-116">Contient une liste de classes de cryptographie qui ont une cartographie à un nom amical dans le \*\* \<nomEntry>\*\* élément.</span><span class="sxs-lookup"><span data-stu-id="e5186-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="e5186-117">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="e5186-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5186-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5186-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e5186-119">Élément</span><span class="sxs-lookup"><span data-stu-id="e5186-119">Element</span></span>|<span data-ttu-id="e5186-120">Description</span><span class="sxs-lookup"><span data-stu-id="e5186-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e5186-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5186-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="e5186-122">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="e5186-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="e5186-123">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="e5186-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="e5186-124">Contient l’élément \<cryptographySettings>.</span><span class="sxs-lookup"><span data-stu-id="e5186-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5186-125"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e5186-125">Example</span></span>  
 <span data-ttu-id="e5186-126">L’exemple suivant montre comment utiliser le \*\* \<cryptoNameMapping>\*\* élément pour référencer une classe de cryptographie et configurer le temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e5186-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="e5186-127">Vous pouvez ensuite passer la chaîne <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> "RSA" <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> à la `MyCryptoRSAClass` méthode et utiliser la méthode pour retourner un objet.</span><span class="sxs-lookup"><span data-stu-id="e5186-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5186-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5186-128">See also</span></span>

- [<span data-ttu-id="e5186-129">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="e5186-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e5186-130">Paramètres de cryptographie Schema</span><span class="sxs-lookup"><span data-stu-id="e5186-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e5186-131">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="e5186-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="e5186-132">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="e5186-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
