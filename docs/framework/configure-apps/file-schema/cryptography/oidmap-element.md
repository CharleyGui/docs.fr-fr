---
title: Élément <oidMap>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: eec2c4745ad5a0492ccf04c8f23b901275f23c01
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698439"
---
# <a name="oidmap-element"></a><span data-ttu-id="00644-102">Élément @no__t 0oidMap ></span><span class="sxs-lookup"><span data-stu-id="00644-102">\<oidMap> Element</span></span>
<span data-ttu-id="00644-103">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="00644-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
[<span data-ttu-id="00644-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="00644-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="00644-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="00644-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="00644-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="00644-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="00644-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="00644-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00644-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00644-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00644-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="00644-109">Attributes and Elements</span></span>  
 <span data-ttu-id="00644-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="00644-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00644-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="00644-111">Attributes</span></span>  
 <span data-ttu-id="00644-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="00644-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="00644-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="00644-113">Child Elements</span></span>  
  
|<span data-ttu-id="00644-114">Élément</span><span class="sxs-lookup"><span data-stu-id="00644-114">Element</span></span>|<span data-ttu-id="00644-115">Description</span><span class="sxs-lookup"><span data-stu-id="00644-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00644-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="00644-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="00644-117">Mappe un OID ASN. 1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="00644-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00644-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="00644-118">Parent Elements</span></span>  
  
|<span data-ttu-id="00644-119">Élément</span><span class="sxs-lookup"><span data-stu-id="00644-119">Element</span></span>|<span data-ttu-id="00644-120">Description</span><span class="sxs-lookup"><span data-stu-id="00644-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="00644-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00644-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="00644-122">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="00644-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="00644-123">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="00644-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00644-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="00644-124">Example</span></span>  
 <span data-ttu-id="00644-125">L’exemple suivant montre comment utiliser l’élément **\<oidMap >** pour contenir un mappage d’un OID pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="00644-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00644-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00644-126">See also</span></span>

- [<span data-ttu-id="00644-127">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="00644-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="00644-128">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="00644-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="00644-129">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="00644-129">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="00644-130">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="00644-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="00644-131">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="00644-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
