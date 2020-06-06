---
title: <remove>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154528"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="618ff-102">\<remove>, élément de \<configSections></span><span class="sxs-lookup"><span data-stu-id="618ff-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="618ff-103">Supprime un groupe de sections ou de sections prédéfini.</span><span class="sxs-lookup"><span data-stu-id="618ff-103">Removes a predefined section or section group.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="618ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="618ff-104">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="618ff-105">Attribut</span><span class="sxs-lookup"><span data-stu-id="618ff-105">Attribute</span></span>

|           | <span data-ttu-id="618ff-106">Description</span><span class="sxs-lookup"><span data-stu-id="618ff-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="618ff-107">**name**</span><span class="sxs-lookup"><span data-stu-id="618ff-107">**name**</span></span>  | <span data-ttu-id="618ff-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="618ff-108">Required attribute.</span></span><br><br><span data-ttu-id="618ff-109">Spécifie le nom de la section ou du groupe de sections à supprimer.</span><span class="sxs-lookup"><span data-stu-id="618ff-109">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="618ff-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="618ff-110">Parent element</span></span>

|     | <span data-ttu-id="618ff-111">Description</span><span class="sxs-lookup"><span data-stu-id="618ff-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="618ff-112">**\<configSections>** Appartient</span><span class="sxs-lookup"><span data-stu-id="618ff-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="618ff-113">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="618ff-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="618ff-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="618ff-114">Child elements</span></span>

<span data-ttu-id="618ff-115">None</span><span class="sxs-lookup"><span data-stu-id="618ff-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="618ff-116">Notes</span><span class="sxs-lookup"><span data-stu-id="618ff-116">Remarks</span></span>

<span data-ttu-id="618ff-117">Vous pouvez utiliser l' **\<remove>** élément pour supprimer de votre application des sections et des groupes de sections qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="618ff-117">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="618ff-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="618ff-118">Example</span></span>

<span data-ttu-id="618ff-119">L’exemple suivant montre comment utiliser l' **\<remove>** élément dans un fichier de configuration de l’application pour supprimer une section précédemment définie dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="618ff-119">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="618ff-120">Le code de fichier de configuration d’ordinateur suivant déclare la section **\<sampleSection>** :</span><span class="sxs-lookup"><span data-stu-id="618ff-120">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="618ff-121">Le code de fichier de configuration de l’application suivant supprime la **\<sampleSection>** section.</span><span class="sxs-lookup"><span data-stu-id="618ff-121">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="618ff-122">Après la suppression, l’application ne peut pas récupérer les paramètres dans **\<sampleSection>** .</span><span class="sxs-lookup"><span data-stu-id="618ff-122">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="618ff-123">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="618ff-123">Configuration file</span></span>

<span data-ttu-id="618ff-124">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="618ff-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="618ff-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="618ff-125">See also</span></span>

- [<span data-ttu-id="618ff-126">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="618ff-126">Configuration file schema for the .NET Framework</span></span>](index.md)
