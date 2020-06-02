---
title: Élément <add> pour <schemaImporterExtensions>
description: L' <add> élément ajoute les types utilisés par la classe XmlSchemaImporter pour le mappage des types XSD aux types .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 6fd8113ad39a22c927035fca574151ae8f002685
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288327"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="3dad9-103">Élément \<add> pour \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="3dad9-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="3dad9-104">Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3dad9-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="3dad9-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="3dad9-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="3dad9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dad9-106">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dad9-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3dad9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3dad9-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3dad9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dad9-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="3dad9-109">Attributes</span></span>  
  
|<span data-ttu-id="3dad9-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="3dad9-110">Attribute</span></span>|<span data-ttu-id="3dad9-111">Description</span><span class="sxs-lookup"><span data-stu-id="3dad9-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3dad9-112">**name**</span><span class="sxs-lookup"><span data-stu-id="3dad9-112">**name**</span></span>|<span data-ttu-id="3dad9-113">Nom simple utilisé pour rechercher l'instance.</span><span class="sxs-lookup"><span data-stu-id="3dad9-113">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="3dad9-114">**type**</span><span class="sxs-lookup"><span data-stu-id="3dad9-114">**type**</span></span>|<span data-ttu-id="3dad9-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3dad9-115">Required.</span></span> <span data-ttu-id="3dad9-116">Spécifie la classe d'extension de schéma à ajouter.</span><span class="sxs-lookup"><span data-stu-id="3dad9-116">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="3dad9-117">La valeur d’attribut **type** doit figurer sur une ligne et inclure le nom complet du type.</span><span class="sxs-lookup"><span data-stu-id="3dad9-117">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="3dad9-118">Lorsque l'assembly est placé dans le Global Assembly Cache (GAC), il doit également inclure la version, la culture et le jeton de clé publique de l'assembly signé.</span><span class="sxs-lookup"><span data-stu-id="3dad9-118">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3dad9-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3dad9-119">Child Elements</span></span>  
 <span data-ttu-id="3dad9-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3dad9-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3dad9-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3dad9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3dad9-122">Élément</span><span class="sxs-lookup"><span data-stu-id="3dad9-122">Element</span></span>|<span data-ttu-id="3dad9-123">Description</span><span class="sxs-lookup"><span data-stu-id="3dad9-123">Description</span></span>|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|<span data-ttu-id="3dad9-124">Contient les types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="3dad9-124">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3dad9-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="3dad9-125">Example</span></span>  
 <span data-ttu-id="3dad9-126">L'exemple de code suivant ajoute un type d'extension que XmlSchemaImporter peut utiliser lors du mappage de types.</span><span class="sxs-lookup"><span data-stu-id="3dad9-126">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3dad9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dad9-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="3dad9-128">\<system.xml.serialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="3dad9-128">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="3dad9-129">\<schemaImporterExtensions>Appartient</span><span class="sxs-lookup"><span data-stu-id="3dad9-129">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
