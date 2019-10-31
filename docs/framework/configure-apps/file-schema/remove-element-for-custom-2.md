---
title: élément <remove> pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc1519a794e24e04074dd2a674ecc2c0f3666521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118565"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="d46f3-102">\<supprimer > élément de NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="d46f3-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="d46f3-103">Supprime un paramètre défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="d46f3-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="d46f3-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d46f3-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="d46f3-105">&nbsp;&nbsp;[ **\<** ](custom-element-2.md) de la  >.</span><span class="sxs-lookup"><span data-stu-id="d46f3-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="d46f3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<supprimer >**</span><span class="sxs-lookup"><span data-stu-id="d46f3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d46f3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d46f3-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="d46f3-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d46f3-108">Attribute</span></span>

|           | <span data-ttu-id="d46f3-109">Description</span><span class="sxs-lookup"><span data-stu-id="d46f3-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d46f3-110">**key**</span><span class="sxs-lookup"><span data-stu-id="d46f3-110">**key**</span></span>   | <span data-ttu-id="d46f3-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="d46f3-111">Required attribute.</span></span><br><br><span data-ttu-id="d46f3-112">Spécifie le nom du paramètre à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d46f3-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d46f3-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="d46f3-113">Parent element</span></span>

| <span data-ttu-id="d46f3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d46f3-114">Element</span></span> | <span data-ttu-id="d46f3-115">Description</span><span class="sxs-lookup"><span data-stu-id="d46f3-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="d46f3-116"> **\<** de la > Appartient</span><span class="sxs-lookup"><span data-stu-id="d46f3-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="d46f3-117">Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="d46f3-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d46f3-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d46f3-118">Child elements</span></span>

<span data-ttu-id="d46f3-119">aucune.</span><span class="sxs-lookup"><span data-stu-id="d46f3-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d46f3-120">Notes</span><span class="sxs-lookup"><span data-stu-id="d46f3-120">Remarks</span></span>

<span data-ttu-id="d46f3-121">Vous pouvez utiliser l’élément **\<supprimer >** pour supprimer de votre application les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="d46f3-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="d46f3-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="d46f3-122">Example</span></span>

<span data-ttu-id="d46f3-123">L’exemple suivant montre comment utiliser la **\<supprimer >** élément dans un fichier de configuration d’application pour supprimer les paramètres précédemment définis dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d46f3-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="d46f3-124">Le code de fichier de configuration d’ordinateur suivant déclare la section **\<> mySection** et y ajoute deux paramètres, `key1` et `key2`:</span><span class="sxs-lookup"><span data-stu-id="d46f3-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="d46f3-125">Le code de fichier de configuration d’application suivant supprime le paramètre `key2` de **\<> mySection**:</span><span class="sxs-lookup"><span data-stu-id="d46f3-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d46f3-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="d46f3-126">Configuration file</span></span>

<span data-ttu-id="d46f3-127">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="d46f3-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d46f3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d46f3-128">See also</span></span>

- [<span data-ttu-id="d46f3-129">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d46f3-129">Configuration file schema for the .NET Framework</span></span>](index.md)
