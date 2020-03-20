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
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155165"
---
# <a name="oidmap-element"></a><span data-ttu-id="0f685-102">\<oidMap> Element</span><span class="sxs-lookup"><span data-stu-id="0f685-102">\<oidMap> Element</span></span>
<span data-ttu-id="0f685-103">Contient des cartographies ASN.1 d’identifiant d’objet (OID) aux classes.</span><span class="sxs-lookup"><span data-stu-id="0f685-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

<span data-ttu-id="0f685-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0f685-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0f685-105">&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0f685-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="0f685-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographieSettings>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="0f685-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="0f685-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="0f685-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0f685-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f685-108">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f685-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0f685-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0f685-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0f685-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f685-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0f685-111">Attributes</span></span>  
 <span data-ttu-id="0f685-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0f685-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0f685-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0f685-113">Child Elements</span></span>  
  
|<span data-ttu-id="0f685-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0f685-114">Element</span></span>|<span data-ttu-id="0f685-115">Description</span><span class="sxs-lookup"><span data-stu-id="0f685-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f685-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="0f685-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="0f685-117">Cartes d’un ASN.1 OID à un nom amical.</span><span class="sxs-lookup"><span data-stu-id="0f685-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f685-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0f685-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0f685-119">Élément</span><span class="sxs-lookup"><span data-stu-id="0f685-119">Element</span></span>|<span data-ttu-id="0f685-120">Description</span><span class="sxs-lookup"><span data-stu-id="0f685-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0f685-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f685-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0f685-122">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="0f685-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="0f685-123">Contient `cryptographySettings` l’élément.</span><span class="sxs-lookup"><span data-stu-id="0f685-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f685-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0f685-124">Example</span></span>  
 <span data-ttu-id="0f685-125">L’exemple suivant montre comment utiliser \*\* \<l’élément oidMap>\*\* pour contenir une cartographie d’un OID pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="0f685-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f685-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f685-126">See also</span></span>

- [<span data-ttu-id="0f685-127">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="0f685-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0f685-128">Paramètres de cryptographie Schema</span><span class="sxs-lookup"><span data-stu-id="0f685-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0f685-129">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="0f685-129">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="0f685-130">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="0f685-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="0f685-131">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="0f685-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
