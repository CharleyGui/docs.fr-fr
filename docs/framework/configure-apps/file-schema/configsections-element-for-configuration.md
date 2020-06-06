---
title: <configSections>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155347"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="a410d-102">\<configSections>, élément de \<configuration></span><span class="sxs-lookup"><span data-stu-id="a410d-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="a410d-103">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="a410d-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="a410d-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="a410d-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="a410d-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="a410d-105">Attributes</span></span>

<span data-ttu-id="a410d-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="a410d-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="a410d-107">Élément parent</span><span class="sxs-lookup"><span data-stu-id="a410d-107">Parent element</span></span>

|     | <span data-ttu-id="a410d-108">Description</span><span class="sxs-lookup"><span data-stu-id="a410d-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="a410d-109">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a410d-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a410d-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a410d-110">Child elements</span></span>

|     | <span data-ttu-id="a410d-111">Description</span><span class="sxs-lookup"><span data-stu-id="a410d-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="a410d-112">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="a410d-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="a410d-113">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="a410d-113">Defines a namespace for configuration sections.</span></span> |
| [**\<remove>**](remove-element-for-configsections.md) | <span data-ttu-id="a410d-114">Supprime un groupe de sections ou de sections prédéfini.</span><span class="sxs-lookup"><span data-stu-id="a410d-114">Removes a predefined section or section group.</span></span> |
| [**\<clear>**](clear-element-for-configsections.md) | <span data-ttu-id="a410d-115">Efface toutes les sections et tous les groupes de sections précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="a410d-115">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a410d-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="a410d-116">Remarks</span></span>

<span data-ttu-id="a410d-117">Si cet élément se trouve dans un fichier de configuration, il doit s’agir du premier élément enfant de l' **\<configuration>** élément.</span><span class="sxs-lookup"><span data-stu-id="a410d-117">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="a410d-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="a410d-118">Example</span></span>

<span data-ttu-id="a410d-119">L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :</span><span class="sxs-lookup"><span data-stu-id="a410d-119">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a410d-120">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="a410d-120">Configuration file</span></span>

<span data-ttu-id="a410d-121">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="a410d-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a410d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a410d-122">See also</span></span>

- [<span data-ttu-id="a410d-123">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a410d-123">Configuration file schema for the .NET Framework</span></span>](index.md)
