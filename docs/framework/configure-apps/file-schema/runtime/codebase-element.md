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
ms.openlocfilehash: a06daa0b2aa5374c9959cbbe778d62856819a40e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663868"
---
# <a name="codebase-element"></a><span data-ttu-id="ac553-102">\<Élément codebais ></span><span class="sxs-lookup"><span data-stu-id="ac553-102">\<codeBase> Element</span></span>

<span data-ttu-id="ac553-103">Spécifie où le common language runtime peut trouver un assembly.</span><span class="sxs-lookup"><span data-stu-id="ac553-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="ac553-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span><span class="sxs-lookup"><span data-stu-id="ac553-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="ac553-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac553-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac553-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ac553-106">Attributes and Elements</span></span>

<span data-ttu-id="ac553-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ac553-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac553-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="ac553-108">Attributes</span></span>

|<span data-ttu-id="ac553-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac553-109">Attribute</span></span>|<span data-ttu-id="ac553-110">Description</span><span class="sxs-lookup"><span data-stu-id="ac553-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="ac553-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ac553-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac553-112">Spécifie l’URL où le runtime peut trouver la version spécifiée de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ac553-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="ac553-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ac553-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac553-114">Spécifie la version de l’assembly à laquelle s’applique le code base.</span><span class="sxs-lookup"><span data-stu-id="ac553-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="ac553-115">Le format d’un numéro de version d’assembly est *major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="ac553-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="ac553-116">Attribut de version</span><span class="sxs-lookup"><span data-stu-id="ac553-116">version Attribute</span></span>

|<span data-ttu-id="ac553-117">`Value`</span><span class="sxs-lookup"><span data-stu-id="ac553-117">Value</span></span>|<span data-ttu-id="ac553-118">Description</span><span class="sxs-lookup"><span data-stu-id="ac553-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="ac553-119">Les valeurs valides pour chaque partie du numéro de version sont comprises entre 0 et 65535.</span><span class="sxs-lookup"><span data-stu-id="ac553-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="ac553-120">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="ac553-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ac553-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ac553-121">Child Elements</span></span>

<span data-ttu-id="ac553-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ac553-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac553-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ac553-123">Parent Elements</span></span>

|<span data-ttu-id="ac553-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ac553-124">Element</span></span>|<span data-ttu-id="ac553-125">Description</span><span class="sxs-lookup"><span data-stu-id="ac553-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="ac553-126">Définit une collection de fournisseurs de générations utilisés pour compiler des fichiers de ressources personnalisés.</span><span class="sxs-lookup"><span data-stu-id="ac553-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="ac553-127">Le nombre de fournisseurs de générations n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="ac553-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="ac553-128">Configure tous les paramètres de compilation utilisés par ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ac553-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="ac553-129">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac553-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="ac553-130">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ac553-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ac553-131">Notes</span><span class="sxs-lookup"><span data-stu-id="ac553-131">Remarks</span></span>

<span data-ttu-id="ac553-132">Pour que le runtime utilise le  **\<** paramètre CODEBASE > dans un fichier de configuration machine ou un fichier de stratégie d’éditeur, le fichier doit également rediriger la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ac553-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="ac553-133">Les fichiers de configuration de l’application peuvent avoir un paramètre code base sans rediriger la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ac553-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="ac553-134">Après avoir déterminé la version de l’assembly à utiliser, le runtime applique le paramètre de code base du fichier qui détermine la version.</span><span class="sxs-lookup"><span data-stu-id="ac553-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="ac553-135">Si aucun code base n’est indiqué, le runtime détecte l’assembly de la façon habituelle.</span><span class="sxs-lookup"><span data-stu-id="ac553-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="ac553-136">Si l’assembly a un nom fort, le paramètre de code base peut se trouver n’importe où sur l’intranet local ou sur Internet.</span><span class="sxs-lookup"><span data-stu-id="ac553-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="ac553-137">Si l’assembly est un assembly privé, le paramètre de code base doit être un chemin d’accès relatif au répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="ac553-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="ac553-138">Pour les assemblys sans nom fort, la version est ignorée et le chargeur utilise la première apparence \<du code base > dans \<le > dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="ac553-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="ac553-139">S’il y a une entrée dans le fichier de configuration de l’application qui redirige la liaison vers un autre assembly, la redirection aura la priorité, même si la version de l’assembly ne correspond pas à la demande de liaison.</span><span class="sxs-lookup"><span data-stu-id="ac553-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="ac553-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac553-140">Example</span></span>

<span data-ttu-id="ac553-141">L’exemple suivant montre comment spécifier où le runtime peut trouver un assembly.</span><span class="sxs-lookup"><span data-stu-id="ac553-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ac553-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac553-142">See also</span></span>

- [<span data-ttu-id="ac553-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ac553-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ac553-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ac553-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ac553-145">Spécification de l'emplacement d'un assembly</span><span class="sxs-lookup"><span data-stu-id="ac553-145">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="ac553-146">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="ac553-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
