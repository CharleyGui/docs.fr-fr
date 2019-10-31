---
title: <remove>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f57dc9279c107ce751f71c2998670ab992db162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118436"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="81138-102">\<supprimer > élément de \<configSections ></span><span class="sxs-lookup"><span data-stu-id="81138-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="81138-103">Supprime un groupe de sections ou de sections prédéfini.</span><span class="sxs-lookup"><span data-stu-id="81138-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="81138-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="81138-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="81138-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="81138-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="81138-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<supprimer >**</span><span class="sxs-lookup"><span data-stu-id="81138-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="81138-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81138-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="81138-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="81138-108">Attribute</span></span>

|           | <span data-ttu-id="81138-109">Description</span><span class="sxs-lookup"><span data-stu-id="81138-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="81138-110">**name**</span><span class="sxs-lookup"><span data-stu-id="81138-110">**name**</span></span>  | <span data-ttu-id="81138-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="81138-111">Required attribute.</span></span><br><br><span data-ttu-id="81138-112">Spécifie le nom de la section ou du groupe de sections à supprimer.</span><span class="sxs-lookup"><span data-stu-id="81138-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="81138-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="81138-113">Parent element</span></span>

|     | <span data-ttu-id="81138-114">Description</span><span class="sxs-lookup"><span data-stu-id="81138-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="81138-115"> **\<configSections >** Appartient</span><span class="sxs-lookup"><span data-stu-id="81138-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="81138-116">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="81138-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="81138-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="81138-117">Child elements</span></span>

<span data-ttu-id="81138-118">aucune.</span><span class="sxs-lookup"><span data-stu-id="81138-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="81138-119">Notes</span><span class="sxs-lookup"><span data-stu-id="81138-119">Remarks</span></span>

<span data-ttu-id="81138-120">Vous pouvez utiliser l’élément **\<supprimer >** pour supprimer de votre application des sections et des groupes de sections qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="81138-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="81138-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="81138-121">Example</span></span>

<span data-ttu-id="81138-122">L’exemple suivant montre comment utiliser l' **\<supprimer >** élément dans un fichier de configuration d’application pour supprimer une section précédemment définie dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="81138-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="81138-123">Le code de fichier de configuration d’ordinateur suivant déclare la section **\<> sampleSection**:</span><span class="sxs-lookup"><span data-stu-id="81138-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="81138-124">Le code de fichier de configuration d’application suivant supprime la section **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="81138-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="81138-125">Après la suppression, l’application ne peut pas récupérer les paramètres dans **\<> sampleSection**.</span><span class="sxs-lookup"><span data-stu-id="81138-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="81138-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="81138-126">Configuration file</span></span>

<span data-ttu-id="81138-127">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="81138-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="81138-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81138-128">See also</span></span>

- [<span data-ttu-id="81138-129">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81138-129">Configuration file schema for the .NET Framework</span></span>](index.md)
