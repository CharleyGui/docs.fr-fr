---
title: Élément <codeBase>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: bd170b817c5ccc337711f8f79968653c29f3eda4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252746"
---
# <a name="codebase-element"></a><span data-ttu-id="980e5-102">\<Élément codebais ></span><span class="sxs-lookup"><span data-stu-id="980e5-102">\<codeBase> Element</span></span>

<span data-ttu-id="980e5-103">Spécifie où le common language runtime peut trouver un assembly.</span><span class="sxs-lookup"><span data-stu-id="980e5-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="980e5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="980e5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="980e5-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="980e5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="980e5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="980e5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="980e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="980e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="980e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<codeBase>**</span><span class="sxs-lookup"><span data-stu-id="980e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**</span></span>

## <a name="syntax"></a><span data-ttu-id="980e5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="980e5-109">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="980e5-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="980e5-110">Attributes and Elements</span></span>

<span data-ttu-id="980e5-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="980e5-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="980e5-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="980e5-112">Attributes</span></span>

|<span data-ttu-id="980e5-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="980e5-113">Attribute</span></span>|<span data-ttu-id="980e5-114">Description</span><span class="sxs-lookup"><span data-stu-id="980e5-114">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="980e5-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="980e5-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="980e5-116">Spécifie l’URL où le runtime peut trouver la version spécifiée de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="980e5-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="980e5-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="980e5-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="980e5-118">Spécifie la version de l’assembly à laquelle s’applique le code base.</span><span class="sxs-lookup"><span data-stu-id="980e5-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="980e5-119">Le format d’un numéro de version d’assembly est *major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="980e5-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="980e5-120">Attribut de version</span><span class="sxs-lookup"><span data-stu-id="980e5-120">version Attribute</span></span>

|<span data-ttu-id="980e5-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="980e5-121">Value</span></span>|<span data-ttu-id="980e5-122">Description</span><span class="sxs-lookup"><span data-stu-id="980e5-122">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="980e5-123">Les valeurs valides pour chaque partie du numéro de version sont comprises entre 0 et 65535.</span><span class="sxs-lookup"><span data-stu-id="980e5-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="980e5-124">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="980e5-124">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="980e5-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="980e5-125">Child Elements</span></span>

<span data-ttu-id="980e5-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="980e5-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="980e5-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="980e5-127">Parent Elements</span></span>

|<span data-ttu-id="980e5-128">Élément</span><span class="sxs-lookup"><span data-stu-id="980e5-128">Element</span></span>|<span data-ttu-id="980e5-129">Description</span><span class="sxs-lookup"><span data-stu-id="980e5-129">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="980e5-130">Définit une collection de fournisseurs de générations utilisés pour compiler des fichiers de ressources personnalisés.</span><span class="sxs-lookup"><span data-stu-id="980e5-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="980e5-131">Le nombre de fournisseurs de générations n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="980e5-131">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="980e5-132">Configure tous les paramètres de compilation utilisés par ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="980e5-132">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="980e5-133">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="980e5-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="980e5-134">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="980e5-134">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="980e5-135">Notes</span><span class="sxs-lookup"><span data-stu-id="980e5-135">Remarks</span></span>

<span data-ttu-id="980e5-136">Pour que le runtime utilise le  **\<paramètre CODEBASE >** dans un fichier de configuration machine ou un fichier de stratégie d’éditeur, le fichier doit également rediriger la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="980e5-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="980e5-137">Les fichiers de configuration de l’application peuvent avoir un paramètre code base sans rediriger la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="980e5-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="980e5-138">Après avoir déterminé la version de l’assembly à utiliser, le runtime applique le paramètre de code base du fichier qui détermine la version.</span><span class="sxs-lookup"><span data-stu-id="980e5-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="980e5-139">Si aucun code base n’est indiqué, le runtime détecte l’assembly de la façon habituelle.</span><span class="sxs-lookup"><span data-stu-id="980e5-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="980e5-140">Si l’assembly a un nom fort, le paramètre de code base peut se trouver n’importe où sur l’intranet local ou sur Internet.</span><span class="sxs-lookup"><span data-stu-id="980e5-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="980e5-141">Si l’assembly est un assembly privé, le paramètre de code base doit être un chemin d’accès relatif au répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="980e5-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="980e5-142">Pour les assemblys sans nom fort, la version est ignorée et le chargeur utilise la première apparence \<du code base > dans \<le > dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="980e5-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="980e5-143">S’il y a une entrée dans le fichier de configuration de l’application qui redirige la liaison vers un autre assembly, la redirection aura la priorité, même si la version de l’assembly ne correspond pas à la demande de liaison.</span><span class="sxs-lookup"><span data-stu-id="980e5-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="980e5-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="980e5-144">Example</span></span>

<span data-ttu-id="980e5-145">L’exemple suivant montre comment spécifier où le runtime peut trouver un assembly.</span><span class="sxs-lookup"><span data-stu-id="980e5-145">The following example shows how to specify where the runtime can find an assembly.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="980e5-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="980e5-146">See also</span></span>

- [<span data-ttu-id="980e5-147">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="980e5-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="980e5-148">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="980e5-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="980e5-149">Spécification de l'emplacement d'un assembly</span><span class="sxs-lookup"><span data-stu-id="980e5-149">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="980e5-150">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="980e5-150">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
