---
title: <sectionGroup>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215262"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="62ff6-102">\<sectionGroup>, élément de \<configSections></span><span class="sxs-lookup"><span data-stu-id="62ff6-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="62ff6-103">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="62ff6-103">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="62ff6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62ff6-104">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="62ff6-105">Attribut</span><span class="sxs-lookup"><span data-stu-id="62ff6-105">Attribute</span></span>

|           | <span data-ttu-id="62ff6-106">Description</span><span class="sxs-lookup"><span data-stu-id="62ff6-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="62ff6-107">**name**</span><span class="sxs-lookup"><span data-stu-id="62ff6-107">**name**</span></span>  | <span data-ttu-id="62ff6-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="62ff6-108">Required attribute.</span></span><br><br><span data-ttu-id="62ff6-109">Spécifie le nom du groupe de sections que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="62ff6-109">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="62ff6-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="62ff6-110">Parent element</span></span>

|     | <span data-ttu-id="62ff6-111">Description</span><span class="sxs-lookup"><span data-stu-id="62ff6-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="62ff6-112">**\<configSections>** Appartient</span><span class="sxs-lookup"><span data-stu-id="62ff6-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="62ff6-113">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="62ff6-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="62ff6-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="62ff6-114">Child elements</span></span>

|     | <span data-ttu-id="62ff6-115">Description</span><span class="sxs-lookup"><span data-stu-id="62ff6-115">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="62ff6-116">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="62ff6-116">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="62ff6-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="62ff6-117">Remarks</span></span>

<span data-ttu-id="62ff6-118">La déclaration d’un groupe de sections crée une étiquette de conteneur pour les sections de configuration et s’assure qu’il n’existe aucun conflit de noms avec les sections de configuration définies par une autre personne.</span><span class="sxs-lookup"><span data-stu-id="62ff6-118">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="62ff6-119">Vous pouvez imbriquer **\<sectionGroup>** des éléments les uns dans les autres.</span><span class="sxs-lookup"><span data-stu-id="62ff6-119">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="62ff6-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="62ff6-120">Example</span></span>

<span data-ttu-id="62ff6-121">L’exemple suivant montre comment déclarer un groupe de sections et déclarer des sections au sein d’un groupe de sections :</span><span class="sxs-lookup"><span data-stu-id="62ff6-121">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="62ff6-122">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="62ff6-122">Configuration file</span></span>

<span data-ttu-id="62ff6-123">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="62ff6-123">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="62ff6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62ff6-124">See also</span></span>

- [<span data-ttu-id="62ff6-125">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62ff6-125">Configuration file schema for the .NET Framework</span></span>](index.md)
