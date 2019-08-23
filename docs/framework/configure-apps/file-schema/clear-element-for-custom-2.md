---
title: <clear>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: fbb689db4abc5d59729d9a4d9807a02a0983d40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927712"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="ad531-102">\<Clear >, élément de NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="ad531-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="ad531-103">Efface tous les paramètres précédemment définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="ad531-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="ad531-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ad531-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="ad531-105">&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="ad531-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="ad531-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="ad531-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ad531-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad531-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="ad531-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="ad531-108">Attributes</span></span>

<span data-ttu-id="ad531-109">Aucun</span><span class="sxs-lookup"><span data-stu-id="ad531-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="ad531-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="ad531-110">Parent element</span></span>

|     | <span data-ttu-id="ad531-111">Description</span><span class="sxs-lookup"><span data-stu-id="ad531-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="ad531-112">élément de >y  **\<** </span><span class="sxs-lookup"><span data-stu-id="ad531-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="ad531-113">Définit des paramètres pour les sections de configuration personnalisées <xref:System.Configuration.DictionarySectionHandler> qui utilisent les <xref:System.Configuration.NameValueSectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="ad531-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ad531-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ad531-114">Child elements</span></span>

<span data-ttu-id="ad531-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="ad531-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ad531-116">Notes</span><span class="sxs-lookup"><span data-stu-id="ad531-116">Remarks</span></span>

<span data-ttu-id="ad531-117">Vous pouvez utiliser l'  **\<élément clear >** pour supprimer de votre application tous les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="ad531-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="ad531-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="ad531-118">Example</span></span>

<span data-ttu-id="ad531-119">Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l'  **\<élément clear >** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans la configuration de l’ordinateur. txt.</span><span class="sxs-lookup"><span data-stu-id="ad531-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="ad531-120">Le code de fichier de configuration d’ordinateur suivant déclare la section  **\<mySection >** :</span><span class="sxs-lookup"><span data-stu-id="ad531-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="ad531-121">Le code de fichier de configuration d’application suivant supprime tous les paramètres de  **\<mySection >** .</span><span class="sxs-lookup"><span data-stu-id="ad531-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="ad531-122">L’application ne peut pas récupérer les paramètres qui ont été déclarés dans la  **\<section de > mySection** du fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad531-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ad531-123">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="ad531-123">Configuration file</span></span>

<span data-ttu-id="ad531-124">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="ad531-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad531-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad531-125">See also</span></span>

- [<span data-ttu-id="ad531-126">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad531-126">Configuration file schema for the .NET Framework</span></span>](index.md)
