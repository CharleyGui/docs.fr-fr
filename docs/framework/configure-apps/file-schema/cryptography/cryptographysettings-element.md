---
title: Élément <cryptographySettings>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: ca0a9a4b37f28eb03f58de4fd9b120cb7e654e0c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088639"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="060b6-102">\<élément cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="060b6-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="060b6-103">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="060b6-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="060b6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="060b6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="060b6-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="060b6-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="060b6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptographySettings** ></span><span class="sxs-lookup"><span data-stu-id="060b6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="060b6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="060b6-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="060b6-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="060b6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="060b6-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="060b6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="060b6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="060b6-110">Attributes</span></span>  
 <span data-ttu-id="060b6-111">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="060b6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="060b6-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="060b6-112">Child Elements</span></span>  
  
|<span data-ttu-id="060b6-113">Élément</span><span class="sxs-lookup"><span data-stu-id="060b6-113">Element</span></span>|<span data-ttu-id="060b6-114">Description</span><span class="sxs-lookup"><span data-stu-id="060b6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="060b6-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="060b6-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="060b6-116">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="060b6-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="060b6-117">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="060b6-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="060b6-118">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="060b6-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="060b6-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="060b6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="060b6-120">Élément</span><span class="sxs-lookup"><span data-stu-id="060b6-120">Element</span></span>|<span data-ttu-id="060b6-121">Description</span><span class="sxs-lookup"><span data-stu-id="060b6-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="060b6-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="060b6-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="060b6-123">Contient l’élément `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="060b6-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="060b6-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="060b6-124">Example</span></span>  
 <span data-ttu-id="060b6-125">L’exemple suivant montre comment utiliser l’élément **\<cryptographySettings >** pour contenir les mappages de noms de chiffrement et les mappages OID.</span><span class="sxs-lookup"><span data-stu-id="060b6-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="060b6-126">Cet exemple configure le runtime afin que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> retourne un objet `MyHashClass` et que la classe `MyCryptoClass` corresponde à l’identificateur d’objet 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="060b6-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="060b6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="060b6-127">See also</span></span>

- [<span data-ttu-id="060b6-128">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="060b6-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="060b6-129">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="060b6-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="060b6-130">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="060b6-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
