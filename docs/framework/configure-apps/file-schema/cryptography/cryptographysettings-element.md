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
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155230"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="4ee66-102">Élément \<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="4ee66-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="4ee66-103">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="4ee66-103">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="4ee66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ee66-104">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ee66-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4ee66-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4ee66-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4ee66-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ee66-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="4ee66-107">Attributes</span></span>  
 <span data-ttu-id="4ee66-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4ee66-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ee66-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4ee66-109">Child Elements</span></span>  
  
|<span data-ttu-id="4ee66-110">Élément</span><span class="sxs-lookup"><span data-stu-id="4ee66-110">Element</span></span>|<span data-ttu-id="4ee66-111">Description</span><span class="sxs-lookup"><span data-stu-id="4ee66-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="4ee66-112">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="4ee66-112">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="4ee66-113">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="4ee66-113">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ee66-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4ee66-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4ee66-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4ee66-115">Element</span></span>|<span data-ttu-id="4ee66-116">Description</span><span class="sxs-lookup"><span data-stu-id="4ee66-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4ee66-117">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ee66-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="4ee66-118">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="4ee66-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4ee66-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="4ee66-119">Example</span></span>  
 <span data-ttu-id="4ee66-120">L’exemple suivant montre comment utiliser l' **\<cryptographySettings>** élément pour contenir des mappages de noms de chiffrement et des mappages OID.</span><span class="sxs-lookup"><span data-stu-id="4ee66-120">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="4ee66-121">Cet exemple configure le runtime afin que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> retourne un `MyHashClass` objet et que la `MyCryptoClass` classe soit mappée à l’identificateur d’objet 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="4ee66-121">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ee66-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ee66-122">See also</span></span>

- [<span data-ttu-id="4ee66-123">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4ee66-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4ee66-124">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="4ee66-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4ee66-125">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="4ee66-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
