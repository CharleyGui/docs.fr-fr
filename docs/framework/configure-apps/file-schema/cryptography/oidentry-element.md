---
title: Élément <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088547"
---
# <a name="oidentry-element"></a><span data-ttu-id="6ade0-102">\<élément oidEntry ></span><span class="sxs-lookup"><span data-stu-id="6ade0-102">\<oidEntry> Element</span></span>
<span data-ttu-id="6ade0-103">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="6ade0-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

<span data-ttu-id="6ade0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ade0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6ade0-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6ade0-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="6ade0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings**](cryptographysettings-element.md) ></span><span class="sxs-lookup"><span data-stu-id="6ade0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="6ade0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**oidMap**](oidmap-element.md) ></span><span class="sxs-lookup"><span data-stu-id="6ade0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="6ade0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="6ade0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6ade0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ade0-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ade0-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6ade0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6ade0-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6ade0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ade0-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="6ade0-112">Attributes</span></span>  
  
|<span data-ttu-id="6ade0-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="6ade0-113">Attribute</span></span>|<span data-ttu-id="6ade0-114">Description</span><span class="sxs-lookup"><span data-stu-id="6ade0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ade0-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="6ade0-115">**OID**</span></span>|<span data-ttu-id="6ade0-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6ade0-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ade0-117">Spécifie l’OID ASN. 1 correspondant à l’algorithme implémenté par votre classe.</span><span class="sxs-lookup"><span data-stu-id="6ade0-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="6ade0-118">**name**</span><span class="sxs-lookup"><span data-stu-id="6ade0-118">**name**</span></span>|<span data-ttu-id="6ade0-119">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6ade0-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ade0-120">Spécifie la valeur de l’attribut **Name** dans la balise [\<élément nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="6ade0-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ade0-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6ade0-121">Child Elements</span></span>  
 <span data-ttu-id="6ade0-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="6ade0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ade0-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6ade0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6ade0-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6ade0-124">Element</span></span>|<span data-ttu-id="6ade0-125">Description</span><span class="sxs-lookup"><span data-stu-id="6ade0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ade0-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ade0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6ade0-127">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6ade0-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="6ade0-128">Contient l’élément `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="6ade0-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="6ade0-129">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="6ade0-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ade0-130">Notes</span><span class="sxs-lookup"><span data-stu-id="6ade0-130">Remarks</span></span>  
 <span data-ttu-id="6ade0-131">Les identificateurs d’objets ASN. 1 identifient les algorithmes dans certains formats de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6ade0-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="6ade0-132">Mappez les identificateurs d’objet à des noms conviviaux pour les algorithmes que vous souhaitez identifier.</span><span class="sxs-lookup"><span data-stu-id="6ade0-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ade0-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="6ade0-133">Example</span></span>  
 <span data-ttu-id="6ade0-134">L’exemple suivant montre comment utiliser l’élément **\<oidEntry >** pour mapper un identificateur d’objet pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="6ade0-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ade0-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ade0-135">See also</span></span>

- [<span data-ttu-id="6ade0-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6ade0-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6ade0-137">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6ade0-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ade0-138">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6ade0-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6ade0-139">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6ade0-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="6ade0-140">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6ade0-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
