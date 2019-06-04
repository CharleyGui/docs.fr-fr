---
title: <add> élément pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 3bbe4ad6559e324db5853b95e797f50a7b908dcb
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301427"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="c47fb-102">\<Ajouter > élément pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="c47fb-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="c47fb-103">Ajoute des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c47fb-103">Adds custom application settings.</span></span> <span data-ttu-id="c47fb-104">Chaque  **\<Ajouter >** balise contient une paire clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="c47fb-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="c47fb-105">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c47fb-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="c47fb-106">&nbsp;&nbsp;[ **\<sectionName>** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="c47fb-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="c47fb-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="c47fb-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c47fb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c47fb-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="c47fb-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c47fb-109">Attributes</span></span>

| <span data-ttu-id="c47fb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="c47fb-110">Attribute</span></span> | <span data-ttu-id="c47fb-111">Description</span><span class="sxs-lookup"><span data-stu-id="c47fb-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c47fb-112">**key**</span><span class="sxs-lookup"><span data-stu-id="c47fb-112">**key**</span></span>   | <span data-ttu-id="c47fb-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c47fb-113">Required attribute.</span></span><br><br><span data-ttu-id="c47fb-114">Spécifie le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c47fb-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="c47fb-115">**value**</span><span class="sxs-lookup"><span data-stu-id="c47fb-115">**value**</span></span> | <span data-ttu-id="c47fb-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c47fb-116">Required attribute.</span></span><br><br><span data-ttu-id="c47fb-117">Spécifie la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c47fb-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c47fb-118">Élément parent</span><span class="sxs-lookup"><span data-stu-id="c47fb-118">Parent element</span></span>

| <span data-ttu-id="c47fb-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c47fb-119">Element</span></span> | <span data-ttu-id="c47fb-120">Description</span><span class="sxs-lookup"><span data-stu-id="c47fb-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="c47fb-121"> *\*\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="c47fb-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="c47fb-122">Définit les paramètres pour les sections de configuration personnalisées qui utilisent le <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="c47fb-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c47fb-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c47fb-123">Child elements</span></span>

<span data-ttu-id="c47fb-124">None</span><span class="sxs-lookup"><span data-stu-id="c47fb-124">None</span></span>

## <a name="example"></a><span data-ttu-id="c47fb-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="c47fb-125">Example</span></span>

<span data-ttu-id="c47fb-126">L’exemple suivant montre comment définir une section de configuration personnalisée et utiliser le  **\<Ajouter >** élément pour placer les paramètres dans la section :</span><span class="sxs-lookup"><span data-stu-id="c47fb-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c47fb-127">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c47fb-127">Configuration file</span></span>

<span data-ttu-id="c47fb-128">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="c47fb-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c47fb-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c47fb-129">See also</span></span>

- [<span data-ttu-id="c47fb-130">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c47fb-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
