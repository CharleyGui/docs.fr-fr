---
title: élément <clear> pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214740"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="bb1b1-102">\<> élément Clear pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="bb1b1-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="bb1b1-103">Efface tous les paramètres précédemment définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="bb1b1-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb1b1-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="bb1b1-105">&nbsp;&nbsp;[ **\<** ](custom-element-2.md) de la\ >.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\</span></span>
<span data-ttu-id="bb1b1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="bb1b1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bb1b1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb1b1-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="bb1b1-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="bb1b1-108">Attributes</span></span>

<span data-ttu-id="bb1b1-109">None</span><span class="sxs-lookup"><span data-stu-id="bb1b1-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="bb1b1-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="bb1b1-110">Parent element</span></span>

|     | <span data-ttu-id="bb1b1-111">Description</span><span class="sxs-lookup"><span data-stu-id="bb1b1-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="bb1b1-112"> **\<** de la > Appartient</span><span class="sxs-lookup"><span data-stu-id="bb1b1-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="bb1b1-113">Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="bb1b1-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bb1b1-114">Child elements</span></span>

<span data-ttu-id="bb1b1-115">None</span><span class="sxs-lookup"><span data-stu-id="bb1b1-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="bb1b1-116">Notes</span><span class="sxs-lookup"><span data-stu-id="bb1b1-116">Remarks</span></span>

<span data-ttu-id="bb1b1-117">Vous pouvez utiliser l’élément **\<clear >** pour supprimer de votre application tous les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="bb1b1-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb1b1-118">Example</span></span>

<span data-ttu-id="bb1b1-119">Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l’élément **\<clear >** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="bb1b1-120">Le code de fichier de configuration d’ordinateur suivant déclare la section **\<> mySection**:</span><span class="sxs-lookup"><span data-stu-id="bb1b1-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="bb1b1-121">Le code de fichier de configuration d’application suivant supprime tous les paramètres de **\<> mySection**.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="bb1b1-122">L’application ne peut pas récupérer les paramètres qui ont été déclarés dans le dans la section **\<mySection >** du fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="bb1b1-123">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="bb1b1-123">Configuration file</span></span>

<span data-ttu-id="bb1b1-124">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="bb1b1-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb1b1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb1b1-125">See also</span></span>

- [<span data-ttu-id="bb1b1-126">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bb1b1-126">Configuration file schema for the .NET Framework</span></span>](index.md)
