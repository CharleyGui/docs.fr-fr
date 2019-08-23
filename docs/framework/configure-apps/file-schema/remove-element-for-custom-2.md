---
title: <remove>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920946"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="14dbf-102">\<supprimer > élément pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="14dbf-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="14dbf-103">Supprime un paramètre défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="14dbf-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="14dbf-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="14dbf-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="14dbf-105">&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="14dbf-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="14dbf-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="14dbf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="14dbf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14dbf-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="14dbf-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="14dbf-108">Attribute</span></span>

|           | <span data-ttu-id="14dbf-109">Description</span><span class="sxs-lookup"><span data-stu-id="14dbf-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="14dbf-110">**key**</span><span class="sxs-lookup"><span data-stu-id="14dbf-110">**key**</span></span>   | <span data-ttu-id="14dbf-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="14dbf-111">Required attribute.</span></span><br><br><span data-ttu-id="14dbf-112">Spécifie le nom du paramètre à supprimer.</span><span class="sxs-lookup"><span data-stu-id="14dbf-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="14dbf-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="14dbf-113">Parent element</span></span>

| <span data-ttu-id="14dbf-114">Élément</span><span class="sxs-lookup"><span data-stu-id="14dbf-114">Element</span></span> | <span data-ttu-id="14dbf-115">Description</span><span class="sxs-lookup"><span data-stu-id="14dbf-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="14dbf-116">élément de >y  **\<** </span><span class="sxs-lookup"><span data-stu-id="14dbf-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="14dbf-117">Définit des paramètres pour les sections de configuration personnalisées <xref:System.Configuration.DictionarySectionHandler> qui utilisent les <xref:System.Configuration.NameValueSectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="14dbf-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="14dbf-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="14dbf-118">Child elements</span></span>

<span data-ttu-id="14dbf-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="14dbf-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="14dbf-120">Notes</span><span class="sxs-lookup"><span data-stu-id="14dbf-120">Remarks</span></span>

<span data-ttu-id="14dbf-121">Vous pouvez utiliser l'  **\<élément remove >** pour supprimer de votre application les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="14dbf-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="14dbf-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="14dbf-122">Example</span></span>

<span data-ttu-id="14dbf-123">L’exemple suivant montre comment utiliser l'  **\<élément remove >** dans un fichier de configuration de l’application pour supprimer des paramètres précédemment définis dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14dbf-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="14dbf-124">Le code de fichier de configuration de l’ordinateur suivant déclare la section  **\<mySection >** et y `key1` ajoute `key2`deux paramètres:</span><span class="sxs-lookup"><span data-stu-id="14dbf-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="14dbf-125">Le code de fichier de configuration de l' `key2` application suivant supprime le paramètre de  **\<mySection >** :</span><span class="sxs-lookup"><span data-stu-id="14dbf-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="14dbf-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="14dbf-126">Configuration file</span></span>

<span data-ttu-id="14dbf-127">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="14dbf-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="14dbf-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14dbf-128">See also</span></span>

- [<span data-ttu-id="14dbf-129">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14dbf-129">Configuration file schema for the .NET Framework</span></span>](index.md)
