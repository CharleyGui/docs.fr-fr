---
title: Élément <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155244"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="d5c00-102">\<cryptoClasses> Element</span><span class="sxs-lookup"><span data-stu-id="d5c00-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="d5c00-103">Contient une liste de classes de cryptographie qui ont une cartographie à un nom amical dans le [ \<nomEntry>](nameentry-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d5c00-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="d5c00-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="d5c00-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="d5c00-105">&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d5c00-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="d5c00-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographieSettings>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="d5c00-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="d5c00-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="d5c00-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="d5c00-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="d5c00-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c00-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5c00-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5c00-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d5c00-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d5c00-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d5c00-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5c00-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="d5c00-112">Attributes</span></span>  
 <span data-ttu-id="d5c00-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d5c00-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d5c00-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d5c00-114">Child Elements</span></span>  
  
|<span data-ttu-id="d5c00-115">Élément</span><span class="sxs-lookup"><span data-stu-id="d5c00-115">Element</span></span>|<span data-ttu-id="d5c00-116">Description</span><span class="sxs-lookup"><span data-stu-id="d5c00-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5c00-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="d5c00-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="d5c00-118">Contient un cours de cryptographie qui a une cartographie à un nom amical dans le \*\* \<nomEntry>\*\* élément.</span><span class="sxs-lookup"><span data-stu-id="d5c00-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5c00-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d5c00-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d5c00-120">Élément</span><span class="sxs-lookup"><span data-stu-id="d5c00-120">Element</span></span>|<span data-ttu-id="d5c00-121">Description</span><span class="sxs-lookup"><span data-stu-id="d5c00-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d5c00-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5c00-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="d5c00-123">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="d5c00-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="d5c00-124">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="d5c00-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="d5c00-125">Contient `cryptographySettings` l’élément.</span><span class="sxs-lookup"><span data-stu-id="d5c00-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d5c00-126"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d5c00-126">Example</span></span>  
 <span data-ttu-id="d5c00-127">L’exemple suivant montre comment utiliser l’élément \*\* \<cryptoClass>\*\* pour référencer une classe de cryptographie et configurer l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d5c00-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="d5c00-128">Vous pouvez ensuite passer la chaîne <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> "RSA" <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> à la `MyCryptoRSAClass` méthode et utiliser la méthode pour retourner un objet.</span><span class="sxs-lookup"><span data-stu-id="d5c00-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5c00-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5c00-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="d5c00-130">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="d5c00-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d5c00-131">Paramètres de cryptographie Schema</span><span class="sxs-lookup"><span data-stu-id="d5c00-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d5c00-132">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="d5c00-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="d5c00-133">System.Security.Cryptography.CryptoConfig.CreateDeName</span><span class="sxs-lookup"><span data-stu-id="d5c00-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="d5c00-134">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="d5c00-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
