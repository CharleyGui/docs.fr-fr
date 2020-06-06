---
title: <remove>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214757"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="a7043-102">\<remove>, élément de NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="a7043-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="a7043-103">Supprime un paramètre défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="a7043-103">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="a7043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7043-104">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="a7043-105">Attribut</span><span class="sxs-lookup"><span data-stu-id="a7043-105">Attribute</span></span>

|           | <span data-ttu-id="a7043-106">Description</span><span class="sxs-lookup"><span data-stu-id="a7043-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a7043-107">**key**</span><span class="sxs-lookup"><span data-stu-id="a7043-107">**key**</span></span>   | <span data-ttu-id="a7043-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="a7043-108">Required attribute.</span></span><br><br><span data-ttu-id="a7043-109">Spécifie le nom du paramètre à supprimer.</span><span class="sxs-lookup"><span data-stu-id="a7043-109">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a7043-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="a7043-110">Parent element</span></span>

| <span data-ttu-id="a7043-111">Élément</span><span class="sxs-lookup"><span data-stu-id="a7043-111">Element</span></span> | <span data-ttu-id="a7043-112">Description</span><span class="sxs-lookup"><span data-stu-id="a7043-112">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="a7043-113">**\<sectionName>** Appartient</span><span class="sxs-lookup"><span data-stu-id="a7043-113">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="a7043-114">Définit des paramètres pour les sections de configuration personnalisées qui utilisent les <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="a7043-114">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a7043-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7043-115">Child elements</span></span>

<span data-ttu-id="a7043-116">None</span><span class="sxs-lookup"><span data-stu-id="a7043-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a7043-117">Notes</span><span class="sxs-lookup"><span data-stu-id="a7043-117">Remarks</span></span>

<span data-ttu-id="a7043-118">Vous pouvez utiliser l' **\<remove>** élément pour supprimer de votre application les paramètres qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="a7043-118">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="a7043-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7043-119">Example</span></span>

<span data-ttu-id="a7043-120">L’exemple suivant montre comment utiliser l' **\<remove>** élément dans un fichier de configuration de l’application pour supprimer des paramètres précédemment définis dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a7043-120">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="a7043-121">Le code de fichier de configuration d’ordinateur suivant déclare la section **\<mySection>** et y ajoute deux paramètres `key1` `key2` :</span><span class="sxs-lookup"><span data-stu-id="a7043-121">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="a7043-122">Le code de fichier de configuration de l’application suivant supprime le `key2` paramètre de **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="a7043-122">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="a7043-123">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="a7043-123">Configuration file</span></span>

<span data-ttu-id="a7043-124">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7043-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7043-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7043-125">See also</span></span>

- [<span data-ttu-id="a7043-126">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a7043-126">Configuration file schema for the .NET Framework</span></span>](index.md)
