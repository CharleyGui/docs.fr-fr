---
title: <clear>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214740"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="95039-102">\<clear>, élément de NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="95039-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="95039-103">Efface tous les paramètres précédemment définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="95039-103">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="95039-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95039-104">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="95039-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="95039-105">Attributes</span></span>

<span data-ttu-id="95039-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="95039-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="95039-107">Élément parent</span><span class="sxs-lookup"><span data-stu-id="95039-107">Parent element</span></span>

|     | <span data-ttu-id="95039-108">Description</span><span class="sxs-lookup"><span data-stu-id="95039-108">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="95039-109">**\<sectionName>** Appartient</span><span class="sxs-lookup"><span data-stu-id="95039-109">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="95039-110">Définit des paramètres pour les sections de configuration personnalisées qui utilisent les <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="95039-110">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="95039-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="95039-111">Child elements</span></span>

<span data-ttu-id="95039-112">None</span><span class="sxs-lookup"><span data-stu-id="95039-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="95039-113">Notes</span><span class="sxs-lookup"><span data-stu-id="95039-113">Remarks</span></span>

<span data-ttu-id="95039-114">Vous pouvez utiliser l' **\<clear>** élément pour supprimer de votre application tous les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="95039-114">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="95039-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="95039-115">Example</span></span>

<span data-ttu-id="95039-116">Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l' **\<clear>** élément dans un fichier de configuration d’application pour effacer les sections précédemment définies dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="95039-116">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="95039-117">Le code de fichier de configuration d’ordinateur suivant déclare la section **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="95039-117">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="95039-118">Le code de fichier de configuration de l’application suivant supprime tous les paramètres de **\<mySection>** .</span><span class="sxs-lookup"><span data-stu-id="95039-118">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="95039-119">L’application ne peut pas récupérer les paramètres qui ont été déclarés dans la **\<mySection>** section du fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="95039-119">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="95039-120">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="95039-120">Configuration file</span></span>

<span data-ttu-id="95039-121">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="95039-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="95039-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95039-122">See also</span></span>

- [<span data-ttu-id="95039-123">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95039-123">Configuration file schema for the .NET Framework</span></span>](index.md)
