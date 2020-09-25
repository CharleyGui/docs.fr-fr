---
title: Élément <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 89b96edcf1da20698cd203e78fa27e644fa69cc3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201822"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="a6433-102">Élément \<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="a6433-102">\<cryptoClasses> Element</span></span>

<span data-ttu-id="a6433-103">Contient une liste de classes de chiffrement qui ont un mappage à un nom convivial dans l' [\<nameEntry>](nameentry-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="a6433-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="a6433-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6433-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6433-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a6433-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a6433-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a6433-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6433-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a6433-107">Attributes</span></span>  

 <span data-ttu-id="a6433-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a6433-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6433-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a6433-109">Child Elements</span></span>  
  
|<span data-ttu-id="a6433-110">Élément</span><span class="sxs-lookup"><span data-stu-id="a6433-110">Element</span></span>|<span data-ttu-id="a6433-111">Description</span><span class="sxs-lookup"><span data-stu-id="a6433-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="a6433-112">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l' **\<nameEntry>** élément.</span><span class="sxs-lookup"><span data-stu-id="a6433-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6433-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a6433-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a6433-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a6433-114">Element</span></span>|<span data-ttu-id="a6433-115">Description</span><span class="sxs-lookup"><span data-stu-id="a6433-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a6433-116">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6433-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="a6433-117">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a6433-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="a6433-118">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="a6433-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="a6433-119">Contient l' `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="a6433-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a6433-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="a6433-120">Example</span></span>  

 <span data-ttu-id="a6433-121">L’exemple suivant montre comment utiliser l' **\<cryptoClass>** élément pour référencer une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="a6433-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="a6433-122">Vous pouvez ensuite passer la chaîne « RSA » à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et utiliser la <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="a6433-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6433-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6433-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="a6433-124">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="a6433-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a6433-125">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a6433-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a6433-126">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a6433-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="a6433-127">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="a6433-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="a6433-128">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a6433-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
