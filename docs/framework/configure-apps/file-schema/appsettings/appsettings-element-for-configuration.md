---
title: <appSettings>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155529"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="8d8a3-102">\<appSettings> élément pour \<la configuration></span><span class="sxs-lookup"><span data-stu-id="8d8a3-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="8d8a3-103">Contient des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-103">Contains custom application settings.</span></span> <span data-ttu-id="8d8a3-104">Il s’agit d’une section de configuration prédéfinie fournie par le cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="8d8a3-105">configuration &nbsp; &nbsp;>[\*\* \<\*\*](../configuration-element.md) \*\* \<appSettings>\*\*</span><span class="sxs-lookup"><span data-stu-id="8d8a3-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8d8a3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d8a3-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="8d8a3-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="8d8a3-107">Attribute</span></span>

|           | <span data-ttu-id="8d8a3-108">Description</span><span class="sxs-lookup"><span data-stu-id="8d8a3-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="8d8a3-109">**Fichier**</span><span class="sxs-lookup"><span data-stu-id="8d8a3-109">**file**</span></span>  | <span data-ttu-id="8d8a3-110">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-110">Optional attribute.</span></span><br><br><span data-ttu-id="8d8a3-111">Spécifie un chemin relatif vers un fichier externe contenant des paramètres de configuration d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="8d8a3-112">Le fichier spécifié contient le même type de paramètres qui sont spécifiés dans \*\* \<l’ajout>**, \*\* \<supprimer>**, et \*\* \<effacer>\*\* éléments et utilise le même format de paire de clé / valeur que ces éléments.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="8d8a3-113">Le chemin spécifié est relatif au fichier de configuration principal.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="8d8a3-114">Pour une application Windows Forms, il s’agit du dossier binaire (tel que */bin/debug),* et non de l’emplacement du fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="8d8a3-115">Pour les applications Web Forms, le chemin est relatif à la racine de l’application, où se trouve le fichier *web.config.*</span><span class="sxs-lookup"><span data-stu-id="8d8a3-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="8d8a3-116">Le temps d’exécution ignore l’attribut si le fichier spécifié ne peut pas être trouvé.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="8d8a3-117">Élément parent</span><span class="sxs-lookup"><span data-stu-id="8d8a3-117">Parent element</span></span>

|     | <span data-ttu-id="8d8a3-118">Description</span><span class="sxs-lookup"><span data-stu-id="8d8a3-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8d8a3-119">\*\* \<configuration>\*\* Élément</span><span class="sxs-lookup"><span data-stu-id="8d8a3-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="8d8a3-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8d8a3-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d8a3-121">Child elements</span></span>

|     | <span data-ttu-id="8d8a3-122">Description</span><span class="sxs-lookup"><span data-stu-id="8d8a3-122">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8d8a3-123">**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="8d8a3-123">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="8d8a3-124">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-124">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="8d8a3-125">**\<clair>**</span><span class="sxs-lookup"><span data-stu-id="8d8a3-125">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="8d8a3-126">Efface tous les paramètres d’application précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-126">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="8d8a3-127">**\<supprimer>**</span><span class="sxs-lookup"><span data-stu-id="8d8a3-127">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="8d8a3-128">Supprime un paramètre d’application précédemment défini.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-128">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8d8a3-129">Notes </span><span class="sxs-lookup"><span data-stu-id="8d8a3-129">Remarks</span></span>

<span data-ttu-id="8d8a3-130">Les \*\* \<appSettings>\*\* élément stockent des informations personnalisées sur la configuration des applications, telles que les chaînes de connexion de base de données, les trajectoires de fichiers, les URL du service Web XML ou toute autre information de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-130">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="8d8a3-131">Les paires de clés/valeurs spécifiées dans les <xref:System.Configuration.ConfigurationSettings> \*\* \<appSettings>\*\* élément sont accessibles dans le code à l’aide de la classe.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-131">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="8d8a3-132">Vous pouvez utiliser l’attribut **de fichier** dans les \*\* \<appSettings>\*\* élément des fichiers *Web.config* et configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-132">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="8d8a3-133">Cet attribut spécifie un fichier de configuration qui fournit des paramètres supplémentaires ou remplace les paramètres spécifiés dans les \*\* \<appSettings>\*\* élément.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-133">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="8d8a3-134">**L’attribut de fichier** peut être utilisé dans les scénarios de développement de l’équipe de contrôle source, par exemple lorsqu’un utilisateur souhaite remplacer les paramètres du projet spécifiés dans un fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-134">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="8d8a3-135">Les fichiers de configuration spécifiés par l’attribut de **fichier** doivent avoir un nœud de racine des \*\* \<appSettings>\*\* plutôt que \*\* \<la configuration>\*\*.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-135">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="8d8a3-136"> Exemple</span><span class="sxs-lookup"><span data-stu-id="8d8a3-136">Example</span></span>

<span data-ttu-id="8d8a3-137">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="8d8a3-137">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="8d8a3-138">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="8d8a3-138">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="8d8a3-139">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="8d8a3-139">Configuration file</span></span>

<span data-ttu-id="8d8a3-140">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.</span><span class="sxs-lookup"><span data-stu-id="8d8a3-140">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d8a3-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d8a3-141">See also</span></span>

- [<span data-ttu-id="8d8a3-142">Schéma de fichier de configuration pour le cadre .NET</span><span class="sxs-lookup"><span data-stu-id="8d8a3-142">Configuration file schema for the .NET Framework</span></span>](../index.md)
