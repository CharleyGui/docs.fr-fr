---
title: <remove>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 7c0173879c692588cc2e15f0b14a5687bb0404fb
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300673"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="afe06-102">\<Supprimer >, élément pour \<configSections ></span><span class="sxs-lookup"><span data-stu-id="afe06-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="afe06-103">Supprime une section prédéfinie ou le groupe de section.</span><span class="sxs-lookup"><span data-stu-id="afe06-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="afe06-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="afe06-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="afe06-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="afe06-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="afe06-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="afe06-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="afe06-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afe06-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="afe06-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="afe06-108">Attribute</span></span>

|           | <span data-ttu-id="afe06-109">Description</span><span class="sxs-lookup"><span data-stu-id="afe06-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="afe06-110">**name**</span><span class="sxs-lookup"><span data-stu-id="afe06-110">**name**</span></span>  | <span data-ttu-id="afe06-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="afe06-111">Required attribute.</span></span><br><br><span data-ttu-id="afe06-112">Spécifie le nom de la section ou le groupe de section à supprimer.</span><span class="sxs-lookup"><span data-stu-id="afe06-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="afe06-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="afe06-113">Parent element</span></span>

|     | <span data-ttu-id="afe06-114">Description</span><span class="sxs-lookup"><span data-stu-id="afe06-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="afe06-115"> *\*\<configSections >** élément</span><span class="sxs-lookup"><span data-stu-id="afe06-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="afe06-116">Contient des déclarations d’espace de noms et de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="afe06-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="afe06-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="afe06-117">Child elements</span></span>

<span data-ttu-id="afe06-118">None</span><span class="sxs-lookup"><span data-stu-id="afe06-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="afe06-119">Notes</span><span class="sxs-lookup"><span data-stu-id="afe06-119">Remarks</span></span>

<span data-ttu-id="afe06-120">Vous pouvez utiliser la  **\<Supprimer >** élément à supprimer des sections et groupes de votre application qui ont été définies à un niveau supérieur dans la hiérarchie de fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="afe06-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="afe06-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="afe06-121">Example</span></span>

<span data-ttu-id="afe06-122">L’exemple suivant montre comment utiliser le  **\<Supprimer >** élément dans un fichier de configuration d’application pour supprimer une section précédemment définie dans le fichier de configuration machine.</span><span class="sxs-lookup"><span data-stu-id="afe06-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="afe06-123">Le code du fichier de configuration machine suivant déclare la section  **\<sampleSection >** :</span><span class="sxs-lookup"><span data-stu-id="afe06-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="afe06-124">Le code suivant du fichier de configuration de l’application supprime le  **\<sampleSection >** section.</span><span class="sxs-lookup"><span data-stu-id="afe06-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="afe06-125">Après la suppression, l’application ne peut pas récupérer les paramètres dans  **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="afe06-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="afe06-126">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="afe06-126">Configuration file</span></span>

<span data-ttu-id="afe06-127">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="afe06-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="afe06-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afe06-128">See also</span></span>

- [<span data-ttu-id="afe06-129">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="afe06-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
