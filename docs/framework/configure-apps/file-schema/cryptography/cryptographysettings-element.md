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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155230"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="23732-102">\<cryptographieSettings> Element</span><span class="sxs-lookup"><span data-stu-id="23732-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="23732-103">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="23732-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="23732-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="23732-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="23732-105">&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="23732-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="23732-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographieSettings>**</span><span class="sxs-lookup"><span data-stu-id="23732-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="23732-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23732-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23732-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="23732-108">Attributes and Elements</span></span>  
 <span data-ttu-id="23732-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="23732-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23732-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="23732-110">Attributes</span></span>  
 <span data-ttu-id="23732-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="23732-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23732-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="23732-112">Child Elements</span></span>  
  
|<span data-ttu-id="23732-113">Élément</span><span class="sxs-lookup"><span data-stu-id="23732-113">Element</span></span>|<span data-ttu-id="23732-114">Description</span><span class="sxs-lookup"><span data-stu-id="23732-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23732-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="23732-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="23732-116">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="23732-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="23732-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="23732-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="23732-118">Contient des cartographies ASN.1 d’identifiant d’objet (OID) aux classes.</span><span class="sxs-lookup"><span data-stu-id="23732-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23732-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="23732-119">Parent Elements</span></span>  
  
|<span data-ttu-id="23732-120">Élément</span><span class="sxs-lookup"><span data-stu-id="23732-120">Element</span></span>|<span data-ttu-id="23732-121">Description</span><span class="sxs-lookup"><span data-stu-id="23732-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="23732-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23732-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="23732-123">Contient `cryptographySettings` l’élément.</span><span class="sxs-lookup"><span data-stu-id="23732-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="23732-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="23732-124">Example</span></span>  
 <span data-ttu-id="23732-125">L’exemple suivant montre comment utiliser les \*\* \<cryptographieSettings>\*\* élément pour contenir des cartographies nominographies et des cartographies OID.</span><span class="sxs-lookup"><span data-stu-id="23732-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="23732-126">Cet exemple configure le temps <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> d’exécution de sorte que renvoie un `MyHashClass` objet et les `MyCryptoClass` cartes de classe à l’identifiant d’objet 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="23732-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23732-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23732-127">See also</span></span>

- [<span data-ttu-id="23732-128">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="23732-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="23732-129">Paramètres de cryptographie Schema</span><span class="sxs-lookup"><span data-stu-id="23732-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="23732-130">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="23732-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
