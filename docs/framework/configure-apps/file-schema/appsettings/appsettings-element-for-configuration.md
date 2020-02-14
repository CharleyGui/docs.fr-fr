---
title: <appSettings>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 47d7648aae08544890a4dd2e42cedbf68a8acc72
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214734"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="f9ac2-102">\<élément > appSettings pour la configuration de \<></span><span class="sxs-lookup"><span data-stu-id="f9ac2-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="f9ac2-103">Contient des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-103">Contains custom application settings.</span></span> <span data-ttu-id="f9ac2-104">Il s’agit d’une section de configuration prédéfinie fournie par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="f9ac2-105">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f9ac2-105">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="f9ac2-106">&nbsp;&nbsp; **\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="f9ac2-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f9ac2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9ac2-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="f9ac2-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9ac2-108">Attribute</span></span>

|           | <span data-ttu-id="f9ac2-109">Description</span><span class="sxs-lookup"><span data-stu-id="f9ac2-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f9ac2-110">**file**</span><span class="sxs-lookup"><span data-stu-id="f9ac2-110">**file**</span></span>  | <span data-ttu-id="f9ac2-111">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-111">Optional attribute.</span></span><br><br><span data-ttu-id="f9ac2-112">Spécifie un chemin d’accès relatif à un fichier externe contenant les paramètres de configuration d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="f9ac2-113">Le fichier spécifié contient le même type de paramètres que ceux spécifiés dans la **\<ajouter des >** , **\<supprimer >** , et **\<effacer** les éléments de > et utilise le même format de paire clé/valeur que ces éléments.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="f9ac2-114">Le chemin d’accès spécifié est relatif au fichier de configuration principal.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="f9ac2-115">Pour une application Windows Forms, il s’agit du dossier binaire (tel que */bin/debug*), et non de l’emplacement du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="f9ac2-116">Pour les applications Web Forms, le chemin d’accès est relatif à la racine de l’application, où se trouve le fichier *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="f9ac2-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="f9ac2-117">Notez que le runtime ignore l’attribut si le fichier spécifié est introuvable.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f9ac2-118">Élément parent</span><span class="sxs-lookup"><span data-stu-id="f9ac2-118">Parent element</span></span>

|     | <span data-ttu-id="f9ac2-119">Description</span><span class="sxs-lookup"><span data-stu-id="f9ac2-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f9ac2-120"> **\<> de configuration** Appartient</span><span class="sxs-lookup"><span data-stu-id="f9ac2-120">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="f9ac2-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f9ac2-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9ac2-122">Child elements</span></span>

|     | <span data-ttu-id="f9ac2-123">Description</span><span class="sxs-lookup"><span data-stu-id="f9ac2-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f9ac2-124"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="f9ac2-124">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="f9ac2-125">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="f9ac2-126"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="f9ac2-126">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="f9ac2-127">Efface tous les paramètres d’application précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="f9ac2-128"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="f9ac2-128">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="f9ac2-129">Supprime un paramètre d’application défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f9ac2-130">Notes</span><span class="sxs-lookup"><span data-stu-id="f9ac2-130">Remarks</span></span>

<span data-ttu-id="f9ac2-131">L’élément **\<appSettings >** stocke des informations de configuration d’application personnalisées, telles que des chaînes de connexion de base de données, des chemins d’accès aux fichiers, des URL de service Web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="f9ac2-132">Les paires clé/valeur spécifiées dans l’élément **\<appSettings >** sont accessibles dans le code à l’aide de la classe <xref:System.Configuration.ConfigurationSettings>.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="f9ac2-133">Vous pouvez utiliser l’attribut **file** dans l’élément **\<appSettings >** des fichiers *Web. config* et de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="f9ac2-134">Cet attribut spécifie un fichier de configuration qui fournit des paramètres supplémentaires ou substitue les paramètres spécifiés dans l’élément **\<appSettings >** .</span><span class="sxs-lookup"><span data-stu-id="f9ac2-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="f9ac2-135">L’attribut de **fichier** peut être utilisé dans les scénarios de développement de l’équipe de contrôle de code source, par exemple lorsqu’un utilisateur souhaite remplacer les paramètres de projet spécifiés dans un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="f9ac2-136">Les fichiers de configuration spécifiés par l’attribut **file** doivent avoir un nœud racine de **\<appSettings >** plutôt que **\<configuration >** .</span><span class="sxs-lookup"><span data-stu-id="f9ac2-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="f9ac2-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9ac2-137">Example</span></span>

<span data-ttu-id="f9ac2-138">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="f9ac2-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="f9ac2-139">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="f9ac2-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="f9ac2-140">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="f9ac2-140">Configuration file</span></span>

<span data-ttu-id="f9ac2-141">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="f9ac2-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9ac2-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9ac2-142">See also</span></span>

- [<span data-ttu-id="f9ac2-143">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f9ac2-143">Configuration file schema for the .NET Framework</span></span>](../index.md)
