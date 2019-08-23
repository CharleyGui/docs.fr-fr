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
ms.openlocfilehash: cbdf6150010ca2dace3f0610d9caa90c2bf52746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921055"
---
# <a name="oidentry-element"></a><span data-ttu-id="26d7a-102">\<oidEntry >, élément</span><span class="sxs-lookup"><span data-stu-id="26d7a-102">\<oidEntry> Element</span></span>
<span data-ttu-id="26d7a-103">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="26d7a-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="26d7a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="26d7a-104">\<configuration></span></span>  
<span data-ttu-id="26d7a-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="26d7a-105">\<mscorlib></span></span>  
<span data-ttu-id="26d7a-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="26d7a-106">\<cryptographySettings></span></span>  
<span data-ttu-id="26d7a-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="26d7a-107">\<oidMap></span></span>  
<span data-ttu-id="26d7a-108">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="26d7a-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d7a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26d7a-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26d7a-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="26d7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="26d7a-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="26d7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26d7a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="26d7a-112">Attributes</span></span>  
  
|<span data-ttu-id="26d7a-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="26d7a-113">Attribute</span></span>|<span data-ttu-id="26d7a-114">Description</span><span class="sxs-lookup"><span data-stu-id="26d7a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26d7a-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="26d7a-115">**OID**</span></span>|<span data-ttu-id="26d7a-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="26d7a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="26d7a-117">Spécifie l’OID ASN. 1 correspondant à l’algorithme implémenté par votre classe.</span><span class="sxs-lookup"><span data-stu-id="26d7a-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="26d7a-118">**name**</span><span class="sxs-lookup"><span data-stu-id="26d7a-118">**name**</span></span>|<span data-ttu-id="26d7a-119">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="26d7a-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="26d7a-120">Spécifie la valeur de l’attribut **Name** dans la [ \<balise > élément nameEntry](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="26d7a-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26d7a-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="26d7a-121">Child Elements</span></span>  
 <span data-ttu-id="26d7a-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="26d7a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26d7a-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="26d7a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="26d7a-124">Élément</span><span class="sxs-lookup"><span data-stu-id="26d7a-124">Element</span></span>|<span data-ttu-id="26d7a-125">Description</span><span class="sxs-lookup"><span data-stu-id="26d7a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="26d7a-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26d7a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="26d7a-127">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="26d7a-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="26d7a-128">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="26d7a-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="26d7a-129">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="26d7a-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26d7a-130">Notes</span><span class="sxs-lookup"><span data-stu-id="26d7a-130">Remarks</span></span>  
 <span data-ttu-id="26d7a-131">Les identificateurs d’objets ASN. 1 identifient les algorithmes dans certains formats de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="26d7a-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="26d7a-132">Mappez les identificateurs d’objet à des noms conviviaux pour les algorithmes que vous souhaitez identifier.</span><span class="sxs-lookup"><span data-stu-id="26d7a-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26d7a-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="26d7a-133">Example</span></span>  
 <span data-ttu-id="26d7a-134">L’exemple suivant montre comment utiliser l'  **\<élément oidEntry >** pour mapper un identificateur d’objet pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="26d7a-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26d7a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26d7a-135">See also</span></span>

- [<span data-ttu-id="26d7a-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="26d7a-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="26d7a-137">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="26d7a-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="26d7a-138">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="26d7a-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="26d7a-139">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="26d7a-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="26d7a-140">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="26d7a-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
