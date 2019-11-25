---
title: <linkedConfiguration> (élément)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087962"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="caae7-102">\<élément linkedConfiguration ></span><span class="sxs-lookup"><span data-stu-id="caae7-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="caae7-103">Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="caae7-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="caae7-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="caae7-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="caae7-105">&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="caae7-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="caae7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration** ></span><span class="sxs-lookup"><span data-stu-id="caae7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="caae7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caae7-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="caae7-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="caae7-108">Attribute</span></span>

|           | <span data-ttu-id="caae7-109">Description</span><span class="sxs-lookup"><span data-stu-id="caae7-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="caae7-110">**href**</span><span class="sxs-lookup"><span data-stu-id="caae7-110">**href**</span></span>  | <span data-ttu-id="caae7-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="caae7-111">Required attribute.</span></span><br><br><span data-ttu-id="caae7-112">URL du fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="caae7-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="caae7-113">Le seul format pris en charge pour l’attribut **href** est `file://`.</span><span class="sxs-lookup"><span data-stu-id="caae7-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="caae7-114">Les fichiers locaux et les fichiers UNC sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="caae7-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="caae7-115">Élément parent</span><span class="sxs-lookup"><span data-stu-id="caae7-115">Parent element</span></span>

|     | <span data-ttu-id="caae7-116">Description</span><span class="sxs-lookup"><span data-stu-id="caae7-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="caae7-117"> **\<assemblyBinding >** Appartient</span><span class="sxs-lookup"><span data-stu-id="caae7-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="caae7-118">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="caae7-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="caae7-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="caae7-119">Child elements</span></span>

<span data-ttu-id="caae7-120">aucune.</span><span class="sxs-lookup"><span data-stu-id="caae7-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="caae7-121">Notes</span><span class="sxs-lookup"><span data-stu-id="caae7-121">Remarks</span></span>

<span data-ttu-id="caae7-122">L’élément **\<linkedConfiguration >** simplifie la maintenance des assemblys de composants.</span><span class="sxs-lookup"><span data-stu-id="caae7-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="caae7-123">Si une ou plusieurs applications utilisent un assembly qui a un fichier de configuration résidant dans un emplacement connu, les fichiers de configuration des applications qui utilisent l’assembly peuvent utiliser l’élément **\<linkedConfiguration >** pour inclure le fichier de configuration de l’assembly, plutôt que d’inclure directement les informations de configuration.</span><span class="sxs-lookup"><span data-stu-id="caae7-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="caae7-124">Lorsque l’assembly de composant est desservi, la mise à jour du fichier de configuration commun fournit des informations de configuration mises à jour à toutes les applications qui utilisent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="caae7-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="caae7-125">L’élément **\<linkedConfiguration >** n’est pas pris en charge pour les applications avec des manifestes côte à côte Windows.</span><span class="sxs-lookup"><span data-stu-id="caae7-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="caae7-126">Les règles suivantes régissent l’utilisation des fichiers de configuration liés :</span><span class="sxs-lookup"><span data-stu-id="caae7-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="caae7-127">Les paramètres dans les fichiers de configuration inclus affectent uniquement la stratégie de liaison du chargeur et sont utilisés uniquement par le chargeur.</span><span class="sxs-lookup"><span data-stu-id="caae7-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="caae7-128">Les fichiers de configuration inclus peuvent avoir des paramètres autres que des stratégies de liaison, mais ces paramètres n’ont aucun effet.</span><span class="sxs-lookup"><span data-stu-id="caae7-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="caae7-129">Le seul format pris en charge pour l’attribut `href` est `file://`.</span><span class="sxs-lookup"><span data-stu-id="caae7-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="caae7-130">Les fichiers locaux et les fichiers UNC sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="caae7-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="caae7-131">Il n’existe aucune contrainte sur le nombre de configurations liées par fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="caae7-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="caae7-132">Tous les fichiers de configuration liés sont fusionnés pour former un fichier, de la même façon que le comportement de laC++directive `#include` en C/.</span><span class="sxs-lookup"><span data-stu-id="caae7-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="caae7-133">L’élément **\<linkedConfiguration >** est autorisé uniquement dans les fichiers de configuration de l’application ; elle est ignorée dans le *fichier machine. config*.</span><span class="sxs-lookup"><span data-stu-id="caae7-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="caae7-134">Les références circulaires sont détectées et arrêtées.</span><span class="sxs-lookup"><span data-stu-id="caae7-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="caae7-135">Autrement dit, si le **\<linkedConfiguration >** éléments d’une série de fichiers de configuration forment une boucle, la boucle est détectée et arrêtée.</span><span class="sxs-lookup"><span data-stu-id="caae7-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="caae7-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="caae7-136">Example</span></span>

<span data-ttu-id="caae7-137">L’exemple suivant montre comment inclure le fichier de configuration à partir du disque dur local :</span><span class="sxs-lookup"><span data-stu-id="caae7-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="caae7-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caae7-138">See also</span></span>

- [<span data-ttu-id="caae7-139"> **\<assemblyBinding >** Appartient</span><span class="sxs-lookup"><span data-stu-id="caae7-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="caae7-140">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="caae7-140">Configuration file schema for the .NET Framework</span></span>](index.md)
