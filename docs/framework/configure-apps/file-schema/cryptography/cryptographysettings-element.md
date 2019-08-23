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
ms.openlocfilehash: 462db50a42e55c0c5a9570317ceeeb0ae69215a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927652"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="a2c60-102">\<cryptographySettings >, élément</span><span class="sxs-lookup"><span data-stu-id="a2c60-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="a2c60-103">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a2c60-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="a2c60-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a2c60-104">\<configuration></span></span>  
<span data-ttu-id="a2c60-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="a2c60-105">\<mscorlib></span></span>  
<span data-ttu-id="a2c60-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="a2c60-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c60-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2c60-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2c60-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a2c60-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a2c60-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a2c60-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2c60-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a2c60-110">Attributes</span></span>  
 <span data-ttu-id="a2c60-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a2c60-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a2c60-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a2c60-112">Child Elements</span></span>  
  
|<span data-ttu-id="a2c60-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a2c60-113">Element</span></span>|<span data-ttu-id="a2c60-114">Description</span><span class="sxs-lookup"><span data-stu-id="a2c60-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2c60-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="a2c60-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="a2c60-116">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="a2c60-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="a2c60-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="a2c60-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="a2c60-118">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="a2c60-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2c60-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a2c60-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a2c60-120">Élément</span><span class="sxs-lookup"><span data-stu-id="a2c60-120">Element</span></span>|<span data-ttu-id="a2c60-121">Description</span><span class="sxs-lookup"><span data-stu-id="a2c60-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a2c60-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2c60-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="a2c60-123">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="a2c60-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a2c60-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2c60-124">Example</span></span>  
 <span data-ttu-id="a2c60-125">L’exemple suivant montre comment utiliser l’élément  **\<cryptographySettings >** pour contenir les mappages de noms de chiffrement et les mappages OID.</span><span class="sxs-lookup"><span data-stu-id="a2c60-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="a2c60-126">Cet exemple configure le runtime afin que retourne <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> un `MyHashClass` objet et que la `MyCryptoClass` classe soit mappée à l’identificateur d’objet 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="a2c60-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2c60-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c60-127">See also</span></span>

- [<span data-ttu-id="a2c60-128">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a2c60-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a2c60-129">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a2c60-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a2c60-130">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="a2c60-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
