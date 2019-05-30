---
title: <sectionGroup>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 750708483f9680745eef4531d86fa7ecaa329f51
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301195"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="f9091-102">\<sectionGroup >, élément pour \<configSections ></span><span class="sxs-lookup"><span data-stu-id="f9091-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="f9091-103">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9091-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="f9091-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f9091-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f9091-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f9091-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f9091-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="f9091-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f9091-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9091-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="f9091-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9091-108">Attribute</span></span>

|           | <span data-ttu-id="f9091-109">Description</span><span class="sxs-lookup"><span data-stu-id="f9091-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f9091-110">**name**</span><span class="sxs-lookup"><span data-stu-id="f9091-110">**name**</span></span>  | <span data-ttu-id="f9091-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f9091-111">Required attribute.</span></span><br><br><span data-ttu-id="f9091-112">Spécifie le nom du groupe de section que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="f9091-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f9091-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="f9091-113">Parent element</span></span>

|     | <span data-ttu-id="f9091-114">Description</span><span class="sxs-lookup"><span data-stu-id="f9091-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f9091-115"> *\*\<configSections >** élément</span><span class="sxs-lookup"><span data-stu-id="f9091-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="f9091-116">Contient des déclarations d’espace de noms et de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9091-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f9091-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9091-117">Child elements</span></span>

|     | <span data-ttu-id="f9091-118">Description</span><span class="sxs-lookup"><span data-stu-id="f9091-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f9091-119"> *\*\<section>** </span><span class="sxs-lookup"><span data-stu-id="f9091-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="f9091-120">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9091-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f9091-121">Notes</span><span class="sxs-lookup"><span data-stu-id="f9091-121">Remarks</span></span>

<span data-ttu-id="f9091-122">Déclaration d’un groupe de section crée une balise de conteneur pour les sections de configuration et permet de s’assurer qu’il n’y a aucun conflit d’affectation de noms avec des sections de configuration définies par quelqu'un d’autre.</span><span class="sxs-lookup"><span data-stu-id="f9091-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="f9091-123">Vous pouvez imbriquer  **\<sectionGroup >** éléments dans d’autres.</span><span class="sxs-lookup"><span data-stu-id="f9091-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="f9091-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9091-124">Example</span></span>

<span data-ttu-id="f9091-125">L’exemple suivant montre comment déclarer un groupe de sections et déclarer des sections dans un groupe de sections :</span><span class="sxs-lookup"><span data-stu-id="f9091-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="f9091-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="f9091-126">Configuration file</span></span>

<span data-ttu-id="f9091-127">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="f9091-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9091-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9091-128">See also</span></span>

- [<span data-ttu-id="f9091-129">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f9091-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
