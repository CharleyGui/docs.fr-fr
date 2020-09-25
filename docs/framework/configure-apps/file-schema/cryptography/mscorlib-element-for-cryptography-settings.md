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
ms.openlocfilehash: 1788205997d0dc49df172c9dfe48faceb8fc3290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201783"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="b17e1-102">Élément \<mscorlib> pour les paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b17e1-102">\<mscorlib> Element for Cryptography Settings</span></span>

<span data-ttu-id="b17e1-103">Contient l' [ \<cryptographySettings> élément](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="b17e1-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="b17e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b17e1-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b17e1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b17e1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b17e1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b17e1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b17e1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b17e1-107">Attributes</span></span>  

 <span data-ttu-id="b17e1-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b17e1-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b17e1-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b17e1-109">Child Elements</span></span>  
  
|<span data-ttu-id="b17e1-110">Élément</span><span class="sxs-lookup"><span data-stu-id="b17e1-110">Element</span></span>|<span data-ttu-id="b17e1-111">Description</span><span class="sxs-lookup"><span data-stu-id="b17e1-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="b17e1-112">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b17e1-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b17e1-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b17e1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b17e1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="b17e1-114">Element</span></span>|<span data-ttu-id="b17e1-115">Description</span><span class="sxs-lookup"><span data-stu-id="b17e1-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b17e1-116">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b17e1-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b17e1-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="b17e1-117">Example</span></span>  

 <span data-ttu-id="b17e1-118">L’exemple suivant montre comment utiliser l' **\<mscorlib>** élément pour référencer une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="b17e1-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="b17e1-119">Vous pouvez ensuite passer la chaîne « RSA » à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et utiliser la <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="b17e1-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b17e1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b17e1-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="b17e1-121">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b17e1-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b17e1-122">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b17e1-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b17e1-123">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b17e1-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b17e1-124">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b17e1-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
