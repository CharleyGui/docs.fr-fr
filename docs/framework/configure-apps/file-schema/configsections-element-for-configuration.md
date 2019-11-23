---
title: <configSections>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6024144b6f12df22369366f04c3cbad02c5011d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119013"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="2fff9-102">\<configSections > élément de configuration de \<></span><span class="sxs-lookup"><span data-stu-id="2fff9-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="2fff9-103">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2fff9-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="2fff9-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2fff9-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="2fff9-105">&nbsp;&nbsp; **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="2fff9-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="2fff9-106">Attributes</span><span class="sxs-lookup"><span data-stu-id="2fff9-106">Attributes</span></span>

<span data-ttu-id="2fff9-107">Aucun</span><span class="sxs-lookup"><span data-stu-id="2fff9-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="2fff9-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="2fff9-108">Parent element</span></span>

|     | <span data-ttu-id="2fff9-109">Description</span><span class="sxs-lookup"><span data-stu-id="2fff9-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2fff9-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2fff9-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="2fff9-111">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2fff9-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2fff9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2fff9-112">Child elements</span></span>

|     | <span data-ttu-id="2fff9-113">Description</span><span class="sxs-lookup"><span data-stu-id="2fff9-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2fff9-114"> **\<section>** </span><span class="sxs-lookup"><span data-stu-id="2fff9-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="2fff9-115">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="2fff9-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="2fff9-116"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="2fff9-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="2fff9-117">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="2fff9-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="2fff9-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="2fff9-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="2fff9-119">Supprime un groupe de sections ou de sections prédéfini.</span><span class="sxs-lookup"><span data-stu-id="2fff9-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="2fff9-120"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="2fff9-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="2fff9-121">Efface toutes les sections et tous les groupes de sections précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="2fff9-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2fff9-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="2fff9-122">Remarks</span></span>

<span data-ttu-id="2fff9-123">Si cet élément se trouve dans un fichier de configuration, il doit s’agir du premier élément enfant de l’élément de **> de configuration\<** .</span><span class="sxs-lookup"><span data-stu-id="2fff9-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="2fff9-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fff9-124">Example</span></span>

<span data-ttu-id="2fff9-125">L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :</span><span class="sxs-lookup"><span data-stu-id="2fff9-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="2fff9-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="2fff9-126">Configuration file</span></span>

<span data-ttu-id="2fff9-127">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="2fff9-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fff9-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fff9-128">See also</span></span>

- [<span data-ttu-id="2fff9-129">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2fff9-129">Configuration file schema for the .NET Framework</span></span>](index.md)
