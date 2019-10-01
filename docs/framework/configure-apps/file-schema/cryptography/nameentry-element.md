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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699781"
---
# <a name="nameentry-element"></a><span data-ttu-id="a4d0e-102">Élément @no__t 0nameEntry ></span><span class="sxs-lookup"><span data-stu-id="a4d0e-102">\<nameEntry> Element</span></span>
<span data-ttu-id="a4d0e-103">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[<span data-ttu-id="a4d0e-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a4d0e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a4d0e-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a4d0e-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="a4d0e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4d0e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="a4d0e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4d0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="a4d0e-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="a4d0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d0e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4d0e-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4d0e-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a4d0e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a4d0e-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4d0e-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a4d0e-112">Attributes</span></span>  
  
|<span data-ttu-id="a4d0e-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="a4d0e-113">Attribute</span></span>|<span data-ttu-id="a4d0e-114">Description</span><span class="sxs-lookup"><span data-stu-id="a4d0e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4d0e-115">**name**</span><span class="sxs-lookup"><span data-stu-id="a4d0e-115">**name**</span></span>|<span data-ttu-id="a4d0e-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a4d0e-117">Spécifie le nom convivial de l’algorithme que la classe de chiffrement implémente.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="a4d0e-118">**class**</span><span class="sxs-lookup"><span data-stu-id="a4d0e-118">**class**</span></span>|<span data-ttu-id="a4d0e-119">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="a4d0e-120">Spécifie la valeur de l’attribut **Name** dans l’élément [\<cryptoClass >](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a4d0e-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4d0e-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a4d0e-121">Child Elements</span></span>  
 <span data-ttu-id="a4d0e-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4d0e-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a4d0e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a4d0e-124">Élément</span><span class="sxs-lookup"><span data-stu-id="a4d0e-124">Element</span></span>|<span data-ttu-id="a4d0e-125">Description</span><span class="sxs-lookup"><span data-stu-id="a4d0e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a4d0e-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="a4d0e-127">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4d0e-128">Notes</span><span class="sxs-lookup"><span data-stu-id="a4d0e-128">Remarks</span></span>  
 <span data-ttu-id="a4d0e-129">L’attribut **Name** peut être le nom de l’une des classes abstraites se trouvant dans l’espace de noms <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="a4d0e-130">Quand vous appelez la méthode **Create** sur une classe de chiffrement abstraite, le nom de la classe abstraite est passé à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="a4d0e-131">**CreateFromName** retourne une instance du type indiqué par l’attribut de **classe** .</span><span class="sxs-lookup"><span data-stu-id="a4d0e-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="a4d0e-132">Si l’attribut **Name** est un nom abrégé, tel que RSA, vous pouvez utiliser ce nom lors de l’appel de la méthode **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="a4d0e-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4d0e-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4d0e-133">Example</span></span>  
 <span data-ttu-id="a4d0e-134">L’exemple suivant montre comment utiliser l’élément **\<nameEntry >** pour faire référence à une classe de chiffrement et configurer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="a4d0e-135">Vous pouvez ensuite passer la chaîne « RSA » à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="a4d0e-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4d0e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4d0e-136">See also</span></span>

- [<span data-ttu-id="a4d0e-137">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a4d0e-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a4d0e-138">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a4d0e-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a4d0e-139">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="a4d0e-139">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="a4d0e-140">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a4d0e-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
