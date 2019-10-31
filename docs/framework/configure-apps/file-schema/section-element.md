---
title: <section> d'élément
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7147173dc9f132fa2dd14d20526d59927a183bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115267"
---
# <a name="section-element"></a><span data-ttu-id="cb26e-102">\<section > élément</span><span class="sxs-lookup"><span data-stu-id="cb26e-102">\<section> element</span></span>

<span data-ttu-id="cb26e-103">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="cb26e-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="cb26e-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cb26e-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="cb26e-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="cb26e-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="cb26e-106">&nbsp;&nbsp;&nbsp;&nbsp;**section\<**</span><span class="sxs-lookup"><span data-stu-id="cb26e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="cb26e-107">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cb26e-107">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="cb26e-108">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="cb26e-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="cb26e-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup**](sectiongroup-element-for-configsections.md) > </span><span class="sxs-lookup"><span data-stu-id="cb26e-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="cb26e-110">&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<**</span><span class="sxs-lookup"><span data-stu-id="cb26e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cb26e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb26e-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="cb26e-112">Attributs requis</span><span class="sxs-lookup"><span data-stu-id="cb26e-112">Required attributes</span></span>

|           | <span data-ttu-id="cb26e-113">Description</span><span class="sxs-lookup"><span data-stu-id="cb26e-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cb26e-114">**name**</span><span class="sxs-lookup"><span data-stu-id="cb26e-114">**name**</span></span>  | <span data-ttu-id="cb26e-115">Spécifie le nom de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="cb26e-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="cb26e-116">**type**</span><span class="sxs-lookup"><span data-stu-id="cb26e-116">**type**</span></span>  | <span data-ttu-id="cb26e-117">Spécifie le nom de la classe de gestionnaire de section de configuration qui lit la section dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cb26e-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="cb26e-118">La valeur de type a la syntaxe « Complete-Class-Handler-Class-Name, simple-assembly-name ».</span><span class="sxs-lookup"><span data-stu-id="cb26e-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="cb26e-119">Le nom d’assembly simple est le nom de fichier racine sans l’extension de fichier *. dll* .</span><span class="sxs-lookup"><span data-stu-id="cb26e-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="cb26e-120">Attributs facultatifs</span><span class="sxs-lookup"><span data-stu-id="cb26e-120">Optional attributes</span></span>

<span data-ttu-id="cb26e-121">Les attributs suivants s’appliquent uniquement aux applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cb26e-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="cb26e-122">Le système de configuration ignore ces attributs pour d’autres types d’applications.</span><span class="sxs-lookup"><span data-stu-id="cb26e-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="cb26e-123">Description</span><span class="sxs-lookup"><span data-stu-id="cb26e-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="cb26e-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="cb26e-124">**allowDefinition**</span></span> | <span data-ttu-id="cb26e-125">Spécifie le fichier de configuration dans lequel la section peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="cb26e-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="cb26e-126">Utilisez l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb26e-126">Use one of the following values:</span></span><br><br><span data-ttu-id="cb26e-127">**Importe**</span><span class="sxs-lookup"><span data-stu-id="cb26e-127">**Everywhere**</span></span><br><span data-ttu-id="cb26e-128">Autorise l’utilisation de la section dans n’importe quel fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cb26e-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="cb26e-129">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="cb26e-129">This is the default.</span></span><br><span data-ttu-id="cb26e-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="cb26e-130">**MachineOnly**</span></span><br><span data-ttu-id="cb26e-131">Autorise uniquement l’utilisation de la section dans le fichier de configuration de l’ordinateur (*machine. config*).</span><span class="sxs-lookup"><span data-stu-id="cb26e-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="cb26e-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="cb26e-132">**MachineToApplication**</span></span><br><span data-ttu-id="cb26e-133">Autorise l’utilisation de la section dans le fichier de configuration de l’ordinateur ou dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="cb26e-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="cb26e-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="cb26e-134">**allowLocation**</span></span>   | <span data-ttu-id="cb26e-135">Détermine si la section peut être utilisée dans le **\<emplacement >** élément.</span><span class="sxs-lookup"><span data-stu-id="cb26e-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="cb26e-136">Utilisez l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb26e-136">Use one of the following values:</span></span><br><br><span data-ttu-id="cb26e-137">**true**</span><span class="sxs-lookup"><span data-stu-id="cb26e-137">**true**</span></span><br><span data-ttu-id="cb26e-138">Autorise l’utilisation de la section dans le **\<emplacement >** élément.</span><span class="sxs-lookup"><span data-stu-id="cb26e-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="cb26e-139">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="cb26e-139">This is the default.</span></span><br><span data-ttu-id="cb26e-140">**false**</span><span class="sxs-lookup"><span data-stu-id="cb26e-140">**false**</span></span><br><span data-ttu-id="cb26e-141">N’autorise pas l’utilisation de la section dans le **\<emplacement >** élément.</span><span class="sxs-lookup"><span data-stu-id="cb26e-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="cb26e-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb26e-142">Parent elements</span></span>

|     | <span data-ttu-id="cb26e-143">Description</span><span class="sxs-lookup"><span data-stu-id="cb26e-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cb26e-144"> **\<configSections >** Appartient</span><span class="sxs-lookup"><span data-stu-id="cb26e-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="cb26e-145">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cb26e-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="cb26e-146"> **\<de sectionGroup >** Appartient</span><span class="sxs-lookup"><span data-stu-id="cb26e-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="cb26e-147">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="cb26e-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="cb26e-148">Une **section\<** élément est un élément enfant de **\<configSections >** ou **\<sectionGroup >** , mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="cb26e-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="cb26e-149">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb26e-149">Child elements</span></span>

<span data-ttu-id="cb26e-150">aucune.</span><span class="sxs-lookup"><span data-stu-id="cb26e-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="cb26e-151">Notes</span><span class="sxs-lookup"><span data-stu-id="cb26e-151">Remarks</span></span>

<span data-ttu-id="cb26e-152">La déclaration d’une section de configuration définit essentiellement un nouvel élément pour le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cb26e-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="cb26e-153">Le nouvel élément contient les paramètres qu’un gestionnaire de section de configuration (autrement dit, une classe qui implémente l’interface <xref:System.Configuration.IConfigurationSectionHandler>) lit.</span><span class="sxs-lookup"><span data-stu-id="cb26e-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="cb26e-154">Les attributs et les éléments enfants d’une section que vous définissez dépendent du gestionnaire de section que vous utilisez pour lire vos paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb26e-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="cb26e-155">La déclaration d’un gestionnaire de section de configuration dans le fichier *machine. config* vous permet d’utiliser la section de configuration dans n’importe quel fichier de configuration d’application sur cet ordinateur, à moins que l’attribut **allowDefinition** spécifie autrement.</span><span class="sxs-lookup"><span data-stu-id="cb26e-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="cb26e-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb26e-156">Example</span></span>

<span data-ttu-id="cb26e-157">L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :</span><span class="sxs-lookup"><span data-stu-id="cb26e-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="cb26e-158">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="cb26e-158">Configuration file</span></span>

<span data-ttu-id="cb26e-159">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="cb26e-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb26e-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb26e-160">See also</span></span>

- [<span data-ttu-id="cb26e-161">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cb26e-161">Configuration file schema for the .NET Framework</span></span>](index.md)
