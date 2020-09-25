---
title: Élément <cryptoClass>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: f7fe6d02b4697af3a1d0d04471a2736045fc9ecc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181802"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="d1ce9-102">Élément \<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="d1ce9-102">\<cryptoClass> Element</span></span>

<span data-ttu-id="d1ce9-103">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l' [\<nameEntry>](nameentry-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="d1ce9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1ce9-104">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1ce9-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1ce9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d1ce9-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1ce9-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1ce9-107">Attributes</span></span>  
  
|<span data-ttu-id="d1ce9-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1ce9-108">Attribute</span></span>|<span data-ttu-id="d1ce9-109">Description</span><span class="sxs-lookup"><span data-stu-id="d1ce9-109">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="d1ce9-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="d1ce9-111">Contient les informations relatives à la classe de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-111">Contains the information for the cryptography class.</span></span> <span data-ttu-id="d1ce9-112">Utilisez cet attribut pour fournir un nom abrégé pour votre classe.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-112">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="d1ce9-113">Vous devez spécifier une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="d1ce9-113">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1ce9-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1ce9-114">Child Elements</span></span>  

 <span data-ttu-id="d1ce9-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1ce9-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1ce9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d1ce9-117">Élément</span><span class="sxs-lookup"><span data-stu-id="d1ce9-117">Element</span></span>|<span data-ttu-id="d1ce9-118">Description</span><span class="sxs-lookup"><span data-stu-id="d1ce9-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d1ce9-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="d1ce9-120">Contient une liste de classes de chiffrement qui ont un mappage à un nom convivial dans l' [\<nameEntry>](nameentry-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-120">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="d1ce9-121">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-121">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="d1ce9-122">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-122">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="d1ce9-123">Contient l' [\<cryptographySettings>](cryptographysettings-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-123">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1ce9-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1ce9-124">Example</span></span>  

 <span data-ttu-id="d1ce9-125">L’exemple suivant montre comment utiliser l' **\<cryptoClass>** élément pour référencer une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-125">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="d1ce9-126">Vous pouvez ensuite passer la chaîne « RSA » à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et utiliser la <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="d1ce9-126">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1ce9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1ce9-127">See also</span></span>

- [<span data-ttu-id="d1ce9-128">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="d1ce9-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d1ce9-129">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="d1ce9-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d1ce9-130">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="d1ce9-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="d1ce9-131">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="d1ce9-131">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
