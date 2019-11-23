---
title: Élément <mscorlib> pour les paramètres de chiffrement
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 4e2159cda5f35b5795804dede09ec17d07d71b23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699745"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="48345-102">\<élément mscorlib > pour les paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="48345-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="48345-103">Contient l' [élément\<cryptographySettings >](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="48345-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="48345-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="48345-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="48345-105">&nbsp;&nbsp; **\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="48345-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48345-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48345-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48345-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="48345-107">Attributes and Elements</span></span>  
 <span data-ttu-id="48345-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="48345-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48345-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="48345-109">Attributes</span></span>  
 <span data-ttu-id="48345-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="48345-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48345-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="48345-111">Child Elements</span></span>  
  
|<span data-ttu-id="48345-112">Élément</span><span class="sxs-lookup"><span data-stu-id="48345-112">Element</span></span>|<span data-ttu-id="48345-113">Description</span><span class="sxs-lookup"><span data-stu-id="48345-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="48345-114">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="48345-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48345-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="48345-115">Parent Elements</span></span>  
  
|<span data-ttu-id="48345-116">Élément</span><span class="sxs-lookup"><span data-stu-id="48345-116">Element</span></span>|<span data-ttu-id="48345-117">Description</span><span class="sxs-lookup"><span data-stu-id="48345-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="48345-118">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48345-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="48345-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="48345-119">Example</span></span>  
 <span data-ttu-id="48345-120">L’exemple suivant montre comment utiliser l’élément **\<mscorlib >** pour référencer une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="48345-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="48345-121">Vous pouvez ensuite passer la chaîne « RSA » à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="48345-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48345-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48345-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="48345-123">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="48345-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="48345-124">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="48345-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="48345-125">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="48345-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="48345-126">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="48345-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
