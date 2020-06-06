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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087962"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="81321-102">\<linkedConfiguration>, élément</span><span class="sxs-lookup"><span data-stu-id="81321-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="81321-103">Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="81321-103">Specifies a configuration file to include.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a><span data-ttu-id="81321-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81321-104">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="81321-105">Attribut</span><span class="sxs-lookup"><span data-stu-id="81321-105">Attribute</span></span>

|           | <span data-ttu-id="81321-106">Description</span><span class="sxs-lookup"><span data-stu-id="81321-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="81321-107">**href**</span><span class="sxs-lookup"><span data-stu-id="81321-107">**href**</span></span>  | <span data-ttu-id="81321-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="81321-108">Required attribute.</span></span><br><br><span data-ttu-id="81321-109">URL du fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="81321-109">The URL of the configuration file to include.</span></span> <span data-ttu-id="81321-110">Le seul format pris en charge pour l’attribut **href** est `file://` .</span><span class="sxs-lookup"><span data-stu-id="81321-110">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="81321-111">Les fichiers locaux et les fichiers UNC sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="81321-111">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="81321-112">Élément parent</span><span class="sxs-lookup"><span data-stu-id="81321-112">Parent element</span></span>

|     | <span data-ttu-id="81321-113">Description</span><span class="sxs-lookup"><span data-stu-id="81321-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="81321-114">**\<assemblyBinding>** Appartient</span><span class="sxs-lookup"><span data-stu-id="81321-114">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="81321-115">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="81321-115">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="81321-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="81321-116">Child elements</span></span>

<span data-ttu-id="81321-117">None</span><span class="sxs-lookup"><span data-stu-id="81321-117">None</span></span>

## <a name="remarks"></a><span data-ttu-id="81321-118">Notes</span><span class="sxs-lookup"><span data-stu-id="81321-118">Remarks</span></span>

<span data-ttu-id="81321-119">L' **\<linkedConfiguration>** élément simplifie la maintenance des assemblys de composant.</span><span class="sxs-lookup"><span data-stu-id="81321-119">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="81321-120">Si une ou plusieurs applications utilisent un assembly qui a un fichier de configuration résidant dans un emplacement connu, les fichiers de configuration des applications qui utilisent l’assembly peuvent utiliser l' **\<linkedConfiguration>** élément pour inclure le fichier de configuration de l’assembly, plutôt que d’inclure directement les informations de configuration.</span><span class="sxs-lookup"><span data-stu-id="81321-120">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="81321-121">Lorsque l’assembly de composant est desservi, la mise à jour du fichier de configuration commun fournit des informations de configuration mises à jour à toutes les applications qui utilisent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="81321-121">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="81321-122">L' **\<linkedConfiguration>** élément n’est pas pris en charge pour les applications avec des manifestes côte à côte Windows.</span><span class="sxs-lookup"><span data-stu-id="81321-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="81321-123">Les règles suivantes régissent l’utilisation des fichiers de configuration liés :</span><span class="sxs-lookup"><span data-stu-id="81321-123">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="81321-124">Les paramètres dans les fichiers de configuration inclus affectent uniquement la stratégie de liaison du chargeur et sont utilisés uniquement par le chargeur.</span><span class="sxs-lookup"><span data-stu-id="81321-124">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="81321-125">Les fichiers de configuration inclus peuvent avoir des paramètres autres que des stratégies de liaison, mais ces paramètres n’ont aucun effet.</span><span class="sxs-lookup"><span data-stu-id="81321-125">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="81321-126">Le seul format pris en charge pour l' `href` attribut est `file://` .</span><span class="sxs-lookup"><span data-stu-id="81321-126">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="81321-127">Les fichiers locaux et les fichiers UNC sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="81321-127">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="81321-128">Il n’existe aucune contrainte sur le nombre de configurations liées par fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="81321-128">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="81321-129">Tous les fichiers de configuration liés sont fusionnés pour former un fichier, de la même façon que le comportement de la `#include` directive en C/C++.</span><span class="sxs-lookup"><span data-stu-id="81321-129">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="81321-130">L' **\<linkedConfiguration>** élément n’est autorisé que dans les fichiers de configuration de l’application ; il est ignoré dans le fichier *machine. config*.</span><span class="sxs-lookup"><span data-stu-id="81321-130">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="81321-131">Les références circulaires sont détectées et arrêtées.</span><span class="sxs-lookup"><span data-stu-id="81321-131">Circular references are detected and terminated.</span></span> <span data-ttu-id="81321-132">Autrement dit, si les **\<linkedConfiguration>** éléments d’une série de fichiers de configuration forment une boucle, la boucle est détectée et arrêtée.</span><span class="sxs-lookup"><span data-stu-id="81321-132">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="81321-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="81321-133">Example</span></span>

<span data-ttu-id="81321-134">L’exemple suivant montre comment inclure le fichier de configuration à partir du disque dur local :</span><span class="sxs-lookup"><span data-stu-id="81321-134">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="81321-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81321-135">See also</span></span>

- [<span data-ttu-id="81321-136">**\<assemblyBinding>** Appartient</span><span class="sxs-lookup"><span data-stu-id="81321-136">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="81321-137">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81321-137">Configuration file schema for the .NET Framework</span></span>](index.md)
