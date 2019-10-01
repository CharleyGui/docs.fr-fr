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
ms.openlocfilehash: 96a8c9accc56274b5cc13dc2a871165857b3a2d9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699822"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="eeba4-102">Élément @no__t 0cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="eeba4-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="eeba4-103">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="eeba4-103">Contains cryptography settings.</span></span>  
  
[<span data-ttu-id="eeba4-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="eeba4-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="eeba4-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="eeba4-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="eeba4-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="eeba4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeba4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eeba4-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eeba4-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eeba4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eeba4-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eeba4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eeba4-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="eeba4-110">Attributes</span></span>  
 <span data-ttu-id="eeba4-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="eeba4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eeba4-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eeba4-112">Child Elements</span></span>  
  
|<span data-ttu-id="eeba4-113">Élément</span><span class="sxs-lookup"><span data-stu-id="eeba4-113">Element</span></span>|<span data-ttu-id="eeba4-114">Description</span><span class="sxs-lookup"><span data-stu-id="eeba4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eeba4-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="eeba4-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="eeba4-116">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="eeba4-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="eeba4-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="eeba4-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="eeba4-118">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="eeba4-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eeba4-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eeba4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="eeba4-120">Élément</span><span class="sxs-lookup"><span data-stu-id="eeba4-120">Element</span></span>|<span data-ttu-id="eeba4-121">Description</span><span class="sxs-lookup"><span data-stu-id="eeba4-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eeba4-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eeba4-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="eeba4-123">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="eeba4-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eeba4-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="eeba4-124">Example</span></span>  
 <span data-ttu-id="eeba4-125">L’exemple suivant montre comment utiliser l’élément **\<cryptographySettings >** pour contenir les mappages de noms de chiffrement et les mappages OID.</span><span class="sxs-lookup"><span data-stu-id="eeba4-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="eeba4-126">Cet exemple configure le runtime afin que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> retourne un objet `MyHashClass` et que la classe `MyCryptoClass` soit mappée à l’identificateur d’objet 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="eeba4-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eeba4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eeba4-127">See also</span></span>

- [<span data-ttu-id="eeba4-128">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="eeba4-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="eeba4-129">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="eeba4-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eeba4-130">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="eeba4-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
