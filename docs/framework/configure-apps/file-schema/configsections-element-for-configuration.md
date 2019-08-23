---
title: <configSections>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927672"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="928db-102">\<élément > configSections pour \<la configuration ></span><span class="sxs-lookup"><span data-stu-id="928db-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="928db-103">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="928db-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="928db-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="928db-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="928db-105">&nbsp;&nbsp; **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="928db-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="928db-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="928db-106">Attributes</span></span>

<span data-ttu-id="928db-107">Aucun</span><span class="sxs-lookup"><span data-stu-id="928db-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="928db-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="928db-108">Parent element</span></span>

|     | <span data-ttu-id="928db-109">Description</span><span class="sxs-lookup"><span data-stu-id="928db-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="928db-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="928db-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="928db-111">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="928db-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="928db-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="928db-112">Child elements</span></span>

|     | <span data-ttu-id="928db-113">Description</span><span class="sxs-lookup"><span data-stu-id="928db-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="928db-114"> **\<section>** </span><span class="sxs-lookup"><span data-stu-id="928db-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="928db-115">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="928db-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="928db-116"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="928db-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="928db-117">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="928db-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="928db-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="928db-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="928db-119">Supprime un groupe de sections ou de sections prédéfini.</span><span class="sxs-lookup"><span data-stu-id="928db-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="928db-120"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="928db-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="928db-121">Efface toutes les sections et tous les groupes de sections précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="928db-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="928db-122">Notes</span><span class="sxs-lookup"><span data-stu-id="928db-122">Remarks</span></span>

<span data-ttu-id="928db-123">Si cet élément se trouve dans un fichier de configuration, il doit s’agir du premier élément  **\<** enfant de l’élément de configuration >.</span><span class="sxs-lookup"><span data-stu-id="928db-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="928db-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="928db-124">Example</span></span>

<span data-ttu-id="928db-125">L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section:</span><span class="sxs-lookup"><span data-stu-id="928db-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="928db-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="928db-126">Configuration file</span></span>

<span data-ttu-id="928db-127">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="928db-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="928db-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="928db-128">See also</span></span>

- [<span data-ttu-id="928db-129">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="928db-129">Configuration file schema for the .NET Framework</span></span>](index.md)
