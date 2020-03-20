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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155347"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="59ee7-102">\<les> élément de configuration \<></span><span class="sxs-lookup"><span data-stu-id="59ee7-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="59ee7-103">Contient la section de configuration et les déclarations d’espace nom.</span><span class="sxs-lookup"><span data-stu-id="59ee7-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="59ee7-104">configuration &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) \*\* \<configSections>\*\*</span><span class="sxs-lookup"><span data-stu-id="59ee7-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="59ee7-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="59ee7-105">Attributes</span></span>

<span data-ttu-id="59ee7-106">None</span><span class="sxs-lookup"><span data-stu-id="59ee7-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="59ee7-107">Élément parent</span><span class="sxs-lookup"><span data-stu-id="59ee7-107">Parent element</span></span>

|     | <span data-ttu-id="59ee7-108">Description</span><span class="sxs-lookup"><span data-stu-id="59ee7-108">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="59ee7-109">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="59ee7-109">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="59ee7-110">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59ee7-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="59ee7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="59ee7-111">Child elements</span></span>

|     | <span data-ttu-id="59ee7-112">Description</span><span class="sxs-lookup"><span data-stu-id="59ee7-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="59ee7-113">**\<section>**</span><span class="sxs-lookup"><span data-stu-id="59ee7-113">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="59ee7-114">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="59ee7-114">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="59ee7-115">**\<sectionGroupe>**</span><span class="sxs-lookup"><span data-stu-id="59ee7-115">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="59ee7-116">Définit un espace de nom pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="59ee7-116">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="59ee7-117">**\<supprimer>**</span><span class="sxs-lookup"><span data-stu-id="59ee7-117">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="59ee7-118">Supprime une section prédéfinie ou un groupe de section.</span><span class="sxs-lookup"><span data-stu-id="59ee7-118">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="59ee7-119">**\<clair>**</span><span class="sxs-lookup"><span data-stu-id="59ee7-119">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="59ee7-120">Efface toutes les sections et les groupes de section précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="59ee7-120">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="59ee7-121">Notes </span><span class="sxs-lookup"><span data-stu-id="59ee7-121">Remarks</span></span>

<span data-ttu-id="59ee7-122">Si cet élément est dans un fichier de configuration, \*\* \<\*\* il doit être le premier élément enfant de la configuration>élément.</span><span class="sxs-lookup"><span data-stu-id="59ee7-122">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="59ee7-123"> Exemple</span><span class="sxs-lookup"><span data-stu-id="59ee7-123">Example</span></span>

<span data-ttu-id="59ee7-124">L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :</span><span class="sxs-lookup"><span data-stu-id="59ee7-124">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="59ee7-125">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="59ee7-125">Configuration file</span></span>

<span data-ttu-id="59ee7-126">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.</span><span class="sxs-lookup"><span data-stu-id="59ee7-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="59ee7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59ee7-127">See also</span></span>

- [<span data-ttu-id="59ee7-128">Schéma de fichier de configuration pour le cadre .NET</span><span class="sxs-lookup"><span data-stu-id="59ee7-128">Configuration file schema for the .NET Framework</span></span>](index.md)
