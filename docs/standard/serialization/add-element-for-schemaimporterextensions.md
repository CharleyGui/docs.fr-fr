---
title: Élément <add> pour <schemaImporterExtensions>
description: L' <add> élément ajoute les types utilisés par la classe XmlSchemaImporter pour le mappage des types XSD aux types .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378478"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="d8f77-103">\<Ajouter> élément pour \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d8f77-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="d8f77-104">Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8f77-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="d8f77-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8f77-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="d8f77-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d8f77-106">\<configuration></span></span>  
<span data-ttu-id="d8f77-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="d8f77-107">\<system.xml.serialization></span></span>  
<span data-ttu-id="d8f77-108">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d8f77-108">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="d8f77-109">\<add></span><span class="sxs-lookup"><span data-stu-id="d8f77-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f77-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8f77-110">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8f77-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d8f77-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d8f77-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d8f77-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8f77-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d8f77-113">Attributes</span></span>  
  
|<span data-ttu-id="d8f77-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="d8f77-114">Attribute</span></span>|<span data-ttu-id="d8f77-115">Description</span><span class="sxs-lookup"><span data-stu-id="d8f77-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8f77-116">**name**</span><span class="sxs-lookup"><span data-stu-id="d8f77-116">**name**</span></span>|<span data-ttu-id="d8f77-117">Nom simple utilisé pour rechercher l'instance.</span><span class="sxs-lookup"><span data-stu-id="d8f77-117">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="d8f77-118">**type**</span><span class="sxs-lookup"><span data-stu-id="d8f77-118">**type**</span></span>|<span data-ttu-id="d8f77-119">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d8f77-119">Required.</span></span> <span data-ttu-id="d8f77-120">Spécifie la classe d'extension de schéma à ajouter.</span><span class="sxs-lookup"><span data-stu-id="d8f77-120">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="d8f77-121">La valeur d’attribut **type** doit figurer sur une ligne et inclure le nom complet du type.</span><span class="sxs-lookup"><span data-stu-id="d8f77-121">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="d8f77-122">Lorsque l'assembly est placé dans le Global Assembly Cache (GAC), il doit également inclure la version, la culture et le jeton de clé publique de l'assembly signé.</span><span class="sxs-lookup"><span data-stu-id="d8f77-122">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8f77-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d8f77-123">Child Elements</span></span>  
 <span data-ttu-id="d8f77-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d8f77-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8f77-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d8f77-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d8f77-126">Élément</span><span class="sxs-lookup"><span data-stu-id="d8f77-126">Element</span></span>|<span data-ttu-id="d8f77-127">Description</span><span class="sxs-lookup"><span data-stu-id="d8f77-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8f77-128">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d8f77-128">\<schemaImporterExtensions></span></span>|<span data-ttu-id="d8f77-129">Contient les types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="d8f77-129">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d8f77-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8f77-130">Example</span></span>  
 <span data-ttu-id="d8f77-131">L'exemple de code suivant ajoute un type d'extension que XmlSchemaImporter peut utiliser lors du mappage de types.</span><span class="sxs-lookup"><span data-stu-id="d8f77-131">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8f77-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8f77-132">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="d8f77-133">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="d8f77-133">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="d8f77-134">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="d8f77-134">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
