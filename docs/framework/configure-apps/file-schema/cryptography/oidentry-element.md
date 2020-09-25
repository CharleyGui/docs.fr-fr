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
ms.openlocfilehash: 2207c934f5864890d9b7a5e22c43a1d53e29aaa5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91187106"
---
# <a name="oidentry-element"></a><span data-ttu-id="721a0-102">Élément \<oidEntry></span><span class="sxs-lookup"><span data-stu-id="721a0-102">\<oidEntry> Element</span></span>

<span data-ttu-id="721a0-103">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="721a0-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="721a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="721a0-104">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="721a0-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="721a0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="721a0-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="721a0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="721a0-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="721a0-107">Attributes</span></span>  
  
|<span data-ttu-id="721a0-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="721a0-108">Attribute</span></span>|<span data-ttu-id="721a0-109">Description</span><span class="sxs-lookup"><span data-stu-id="721a0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="721a0-110">**OID**</span><span class="sxs-lookup"><span data-stu-id="721a0-110">**OID**</span></span>|<span data-ttu-id="721a0-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="721a0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="721a0-112">Spécifie l’OID ASN. 1 correspondant à l’algorithme implémenté par votre classe.</span><span class="sxs-lookup"><span data-stu-id="721a0-112">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="721a0-113">**name**</span><span class="sxs-lookup"><span data-stu-id="721a0-113">**name**</span></span>|<span data-ttu-id="721a0-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="721a0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="721a0-115">Spécifie la valeur de l’attribut **Name** dans la [\<nameEntry>](nameentry-element.md) balise.</span><span class="sxs-lookup"><span data-stu-id="721a0-115">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="721a0-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="721a0-116">Child Elements</span></span>  

 <span data-ttu-id="721a0-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="721a0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="721a0-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="721a0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="721a0-119">Élément</span><span class="sxs-lookup"><span data-stu-id="721a0-119">Element</span></span>|<span data-ttu-id="721a0-120">Description</span><span class="sxs-lookup"><span data-stu-id="721a0-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="721a0-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="721a0-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="721a0-122">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="721a0-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="721a0-123">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="721a0-123">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="721a0-124">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="721a0-124">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="721a0-125">Notes</span><span class="sxs-lookup"><span data-stu-id="721a0-125">Remarks</span></span>  

 <span data-ttu-id="721a0-126">Les identificateurs d’objets ASN. 1 identifient les algorithmes dans certains formats de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="721a0-126">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="721a0-127">Mappez les identificateurs d’objet à des noms conviviaux pour les algorithmes que vous souhaitez identifier.</span><span class="sxs-lookup"><span data-stu-id="721a0-127">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="721a0-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="721a0-128">Example</span></span>  

 <span data-ttu-id="721a0-129">L’exemple suivant montre comment utiliser l' **\<oidEntry>** élément pour mapper un identificateur d’objet pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="721a0-129">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="721a0-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="721a0-130">See also</span></span>

- [<span data-ttu-id="721a0-131">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="721a0-131">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="721a0-132">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="721a0-132">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="721a0-133">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="721a0-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="721a0-134">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="721a0-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="721a0-135">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="721a0-135">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
