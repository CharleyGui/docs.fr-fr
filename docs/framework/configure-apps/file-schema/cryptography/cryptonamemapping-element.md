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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155217"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="af6c0-102">Élément \<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="af6c0-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="af6c0-103">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="af6c0-103">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="af6c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af6c0-104">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af6c0-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="af6c0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="af6c0-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="af6c0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af6c0-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="af6c0-107">Attributes</span></span>  
 <span data-ttu-id="af6c0-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="af6c0-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="af6c0-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="af6c0-109">Child Elements</span></span>  
  
|<span data-ttu-id="af6c0-110">Élément</span><span class="sxs-lookup"><span data-stu-id="af6c0-110">Element</span></span>|<span data-ttu-id="af6c0-111">Description</span><span class="sxs-lookup"><span data-stu-id="af6c0-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="af6c0-112">Contient une liste de classes de chiffrement qui ont un mappage à un nom convivial dans l' **\<nameEntry>** élément.</span><span class="sxs-lookup"><span data-stu-id="af6c0-112">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="af6c0-113">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="af6c0-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af6c0-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="af6c0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="af6c0-115">Élément</span><span class="sxs-lookup"><span data-stu-id="af6c0-115">Element</span></span>|<span data-ttu-id="af6c0-116">Description</span><span class="sxs-lookup"><span data-stu-id="af6c0-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="af6c0-117">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af6c0-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="af6c0-118">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="af6c0-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="af6c0-119">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="af6c0-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="af6c0-120">Contient l' \<cryptographySettings> élément.</span><span class="sxs-lookup"><span data-stu-id="af6c0-120">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af6c0-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="af6c0-121">Example</span></span>  
 <span data-ttu-id="af6c0-122">L’exemple suivant montre comment utiliser l' **\<cryptoNameMapping>** élément pour référencer une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="af6c0-122">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="af6c0-123">Vous pouvez ensuite passer la chaîne « RSA » à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et utiliser la <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="af6c0-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af6c0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af6c0-124">See also</span></span>

- [<span data-ttu-id="af6c0-125">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="af6c0-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="af6c0-126">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="af6c0-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="af6c0-127">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="af6c0-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="af6c0-128">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="af6c0-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
