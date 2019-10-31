---
title: élément <clear> pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e27bb7e21baf2eb4990d0107db4aae1b5f9a7d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119076"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="30b26-102">\<> élément Clear pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="30b26-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="30b26-103">Efface tous les paramètres précédemment définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="30b26-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="30b26-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="30b26-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="30b26-105">&nbsp;&nbsp;[ **\<** ](custom-element-2.md) de la  >.</span><span class="sxs-lookup"><span data-stu-id="30b26-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="30b26-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="30b26-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="30b26-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30b26-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="30b26-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="30b26-108">Attributes</span></span>

<span data-ttu-id="30b26-109">aucune.</span><span class="sxs-lookup"><span data-stu-id="30b26-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="30b26-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="30b26-110">Parent element</span></span>

|     | <span data-ttu-id="30b26-111">Description</span><span class="sxs-lookup"><span data-stu-id="30b26-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="30b26-112"> **\<** de la > Appartient</span><span class="sxs-lookup"><span data-stu-id="30b26-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="30b26-113">Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="30b26-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="30b26-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="30b26-114">Child elements</span></span>

<span data-ttu-id="30b26-115">aucune.</span><span class="sxs-lookup"><span data-stu-id="30b26-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="30b26-116">Notes</span><span class="sxs-lookup"><span data-stu-id="30b26-116">Remarks</span></span>

<span data-ttu-id="30b26-117">Vous pouvez utiliser l’élément **\<clear >** pour supprimer de votre application tous les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="30b26-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="30b26-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="30b26-118">Example</span></span>

<span data-ttu-id="30b26-119">Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l’élément **\<clear >** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="30b26-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="30b26-120">Le code de fichier de configuration d’ordinateur suivant déclare la section **\<> mySection**:</span><span class="sxs-lookup"><span data-stu-id="30b26-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="30b26-121">Le code de fichier de configuration d’application suivant supprime tous les paramètres de **\<> mySection**.</span><span class="sxs-lookup"><span data-stu-id="30b26-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="30b26-122">L’application ne peut pas récupérer les paramètres qui ont été déclarés dans le dans la section **\<mySection >** du fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="30b26-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="30b26-123">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="30b26-123">Configuration file</span></span>

<span data-ttu-id="30b26-124">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="30b26-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="30b26-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30b26-125">See also</span></span>

- [<span data-ttu-id="30b26-126">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="30b26-126">Configuration file schema for the .NET Framework</span></span>](index.md)
