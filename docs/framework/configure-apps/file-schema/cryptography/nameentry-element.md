---
title: Élément <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71699781"
---
# <a name="nameentry-element"></a><span data-ttu-id="7e774-102">Élément \<nameEntry></span><span class="sxs-lookup"><span data-stu-id="7e774-102">\<nameEntry> Element</span></span>
<span data-ttu-id="7e774-103">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="7e774-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="7e774-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e774-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e774-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7e774-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7e774-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7e774-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e774-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7e774-107">Attributes</span></span>  
  
|<span data-ttu-id="7e774-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7e774-108">Attribute</span></span>|<span data-ttu-id="7e774-109">Description</span><span class="sxs-lookup"><span data-stu-id="7e774-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e774-110">**name**</span><span class="sxs-lookup"><span data-stu-id="7e774-110">**name**</span></span>|<span data-ttu-id="7e774-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="7e774-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="7e774-112">Spécifie le nom convivial de l’algorithme que la classe de chiffrement implémente.</span><span class="sxs-lookup"><span data-stu-id="7e774-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="7e774-113">**type**</span><span class="sxs-lookup"><span data-stu-id="7e774-113">**class**</span></span>|<span data-ttu-id="7e774-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="7e774-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7e774-115">Spécifie la valeur de l’attribut **Name** dans l' [\<cryptoClass>](cryptoclass-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="7e774-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e774-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7e774-116">Child Elements</span></span>  
 <span data-ttu-id="7e774-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7e774-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e774-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7e774-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7e774-119">Élément</span><span class="sxs-lookup"><span data-stu-id="7e774-119">Element</span></span>|<span data-ttu-id="7e774-120">Description</span><span class="sxs-lookup"><span data-stu-id="7e774-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7e774-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e774-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="7e774-122">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7e774-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e774-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e774-123">Remarks</span></span>  
 <span data-ttu-id="7e774-124">L’attribut **Name** peut être le nom de l’une des classes abstraites trouvées dans l' <xref:System.Security.Cryptography> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7e774-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="7e774-125">Quand vous appelez la méthode **Create** sur une classe de chiffrement abstraite, le nom de la classe abstraite est passé à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="7e774-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="7e774-126">**CreateFromName** retourne une instance du type indiqué par l’attribut de **classe** .</span><span class="sxs-lookup"><span data-stu-id="7e774-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="7e774-127">Si l’attribut **Name** est un nom abrégé, tel que RSA, vous pouvez utiliser ce nom lors de l’appel de la méthode **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="7e774-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e774-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e774-128">Example</span></span>  
 <span data-ttu-id="7e774-129">L’exemple suivant montre comment utiliser l' **\<nameEntry>** élément pour référencer une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="7e774-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7e774-130">Vous pouvez ensuite passer la chaîne « RSA » à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et utiliser la <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="7e774-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e774-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e774-131">See also</span></span>

- [<span data-ttu-id="7e774-132">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7e774-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7e774-133">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="7e774-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7e774-134">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="7e774-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7e774-135">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="7e774-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
