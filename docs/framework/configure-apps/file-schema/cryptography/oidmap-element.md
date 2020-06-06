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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155165"
---
# <a name="oidmap-element"></a><span data-ttu-id="ca3e8-102">Élément \<oidMap></span><span class="sxs-lookup"><span data-stu-id="ca3e8-102">\<oidMap> Element</span></span>
<span data-ttu-id="ca3e8-103">Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="ca3e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca3e8-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca3e8-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ca3e8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ca3e8-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca3e8-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ca3e8-107">Attributes</span></span>  
 <span data-ttu-id="ca3e8-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca3e8-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca3e8-109">Child Elements</span></span>  
  
|<span data-ttu-id="ca3e8-110">Élément</span><span class="sxs-lookup"><span data-stu-id="ca3e8-110">Element</span></span>|<span data-ttu-id="ca3e8-111">Description</span><span class="sxs-lookup"><span data-stu-id="ca3e8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="ca3e8-112">Mappe un OID ASN. 1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca3e8-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca3e8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ca3e8-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ca3e8-114">Element</span></span>|<span data-ttu-id="ca3e8-115">Description</span><span class="sxs-lookup"><span data-stu-id="ca3e8-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca3e8-116">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ca3e8-117">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="ca3e8-118">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ca3e8-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca3e8-119">Example</span></span>  
 <span data-ttu-id="ca3e8-120">L’exemple suivant montre comment utiliser l' **\<oidMap>** élément pour contenir un mappage d’un OID pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="ca3e8-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca3e8-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca3e8-121">See also</span></span>

- [<span data-ttu-id="ca3e8-122">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ca3e8-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ca3e8-123">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="ca3e8-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ca3e8-124">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="ca3e8-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ca3e8-125">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="ca3e8-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="ca3e8-126">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="ca3e8-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
