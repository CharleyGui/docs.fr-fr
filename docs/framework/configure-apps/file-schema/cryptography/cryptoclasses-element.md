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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155244"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="024de-102">Élément \<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="024de-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="024de-103">Contient une liste de classes de chiffrement qui ont un mappage à un nom convivial dans l' [\<nameEntry>](nameentry-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="024de-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="024de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="024de-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="024de-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="024de-105">Attributes and Elements</span></span>  
 <span data-ttu-id="024de-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="024de-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="024de-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="024de-107">Attributes</span></span>  
 <span data-ttu-id="024de-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="024de-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="024de-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="024de-109">Child Elements</span></span>  
  
|<span data-ttu-id="024de-110">Élément</span><span class="sxs-lookup"><span data-stu-id="024de-110">Element</span></span>|<span data-ttu-id="024de-111">Description</span><span class="sxs-lookup"><span data-stu-id="024de-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="024de-112">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l' **\<nameEntry>** élément.</span><span class="sxs-lookup"><span data-stu-id="024de-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="024de-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="024de-113">Parent Elements</span></span>  
  
|<span data-ttu-id="024de-114">Élément</span><span class="sxs-lookup"><span data-stu-id="024de-114">Element</span></span>|<span data-ttu-id="024de-115">Description</span><span class="sxs-lookup"><span data-stu-id="024de-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="024de-116">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="024de-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="024de-117">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="024de-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="024de-118">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="024de-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="024de-119">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="024de-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="024de-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="024de-120">Example</span></span>  
 <span data-ttu-id="024de-121">L’exemple suivant montre comment utiliser l' **\<cryptoClass>** élément pour référencer une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="024de-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="024de-122">Vous pouvez ensuite passer la chaîne « RSA » à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et utiliser la <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="024de-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="024de-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="024de-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="024de-124">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="024de-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="024de-125">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="024de-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="024de-126">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="024de-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="024de-127">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="024de-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="024de-128">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="024de-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
