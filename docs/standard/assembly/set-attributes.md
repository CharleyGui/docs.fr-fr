---
title: Définir des attributs d’assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: fe003a6c74da59c1cb47a0f12a8597143916e320
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138629"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="ae1eb-102">Définir des attributs d’assembly</span><span class="sxs-lookup"><span data-stu-id="ae1eb-102">Set assembly attributes</span></span>

<span data-ttu-id="ae1eb-103">Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-103">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="ae1eb-104">Les attributs sont répartis selon les ensembles d’informations suivants :</span><span class="sxs-lookup"><span data-stu-id="ae1eb-104">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="ae1eb-105">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="ae1eb-105">Assembly identity attributes</span></span>

- <span data-ttu-id="ae1eb-106">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="ae1eb-106">Informational attributes</span></span>

- <span data-ttu-id="ae1eb-107">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="ae1eb-107">Assembly manifest attributes</span></span>

- <span data-ttu-id="ae1eb-108">Attributs de nom fort</span><span class="sxs-lookup"><span data-stu-id="ae1eb-108">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="ae1eb-109">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="ae1eb-109">Assembly identity attributes</span></span>

<span data-ttu-id="ae1eb-110">Trois attributs avec un nom fort (le cas échéant), déterminent l’identité d’un assembly : nom, version et culture.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-110">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="ae1eb-111">Ces attributs constituent le nom complet de l’assembly et sont requis lorsque vous référencez l’assembly dans le code.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-111">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="ae1eb-112">Vous pouvez utiliser les attributs pour définir la version et la culture d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-112">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="ae1eb-113">Le compilateur ou l’utilitaire [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) définit la valeur du nom lors de la création de l’assembly, en fonction du fichier contenant le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-113">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="ae1eb-114">Le tableau suivant décrit les attributs de version et de culture.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-114">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="ae1eb-115">Attribut d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="ae1eb-115">Assembly identity attribute</span></span>|<span data-ttu-id="ae1eb-116">Description</span><span class="sxs-lookup"><span data-stu-id="ae1eb-116">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="ae1eb-117">Champ énuméré désignant la culture que l’assembly prend en charge.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-117">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="ae1eb-118">Un assembly peut également spécifier une indépendance de culture, indiquant qu’il contient les ressources pour la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-118">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="ae1eb-119">**Remarque :** Le runtime gère tout assembly qui n’a pas l’attribut de culture défini avec la valeur Null comme un assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-119">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="ae1eb-120">Ces assemblys sont soumis aux règles de liaison d’assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-120">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="ae1eb-121">Pour plus d’informations, consultez [Comment le runtime localise les assemblys](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ae1eb-121">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="ae1eb-122">Valeur qui définit les attributs d’assembly, par exemple l’exécution côte à côte de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-122">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="ae1eb-123">Valeur numérique au format *version principale*.*version secondaire*.*build*.*révision* (p. ex. 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="ae1eb-123">Numeric value in the format *major*.*minor*.*build*.*revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="ae1eb-124">Le common language runtime utilise cette valeur pour effectuer les opérations de liaison dans les assemblys avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-124">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="ae1eb-125">**Remarque :** Si l’attribut <xref:System.Reflection.AssemblyInformationalVersionAttribute> n’est pas appliqué à un assembly, le numéro de version spécifié par l’attribut <xref:System.Reflection.AssemblyVersionAttribute> est utilisé par les propriétés <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-125">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="ae1eb-126">L’exemple de code suivant montre comment appliquer les attributs de version et de culture à un assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-126">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a><span data-ttu-id="ae1eb-127">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="ae1eb-127">Informational attributes</span></span>

<span data-ttu-id="ae1eb-128">Vous pouvez utiliser les attributs d’informations pour fournir des informations supplémentaires sur le produit ou la société de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-128">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="ae1eb-129">Le tableau suivant décrit les attributs d’informations que vous pouvez appliquer à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-129">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="ae1eb-130">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="ae1eb-130">Informational attribute</span></span>|<span data-ttu-id="ae1eb-131">Description</span><span class="sxs-lookup"><span data-stu-id="ae1eb-131">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="ae1eb-132">Valeur de chaîne qui spécifie un nom de société.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-132">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="ae1eb-133">Valeur de chaîne qui spécifie les informations de copyright.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-133">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="ae1eb-134">Valeur de chaîne qui spécifie le numéro de version du fichier Win32.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-134">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="ae1eb-135">Par défaut, il s’agit normalement de la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-135">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="ae1eb-136">Valeur de chaîne qui spécifie les informations de version qui ne sont pas utilisées par le common language runtime, comme un numéro de version du produit complet.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-136">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="ae1eb-137">**Remarque :** Si cet attribut est appliqué à un assembly, la chaîne qu’il spécifie peut être obtenue au moment de l’exécution à l’aide de la propriété <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-137">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ae1eb-138">Cette chaîne est également utilisée dans le chemin d’accès et la clé de Registre fournis par les propriétés <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-138">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="ae1eb-139">Valeur de chaîne qui spécifie les informations de produit.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-139">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="ae1eb-140">Valeur de chaîne qui spécifie les informations de marque.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-140">String value specifying trademark information.</span></span>|

<span data-ttu-id="ae1eb-141">Ces attributs peuvent apparaître sur la page Propriétés Windows de l’assembly, ou ils peuvent être remplacés à l’aide de l’option **/win32res** du compilateur pour spécifier votre propre fichier de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-141">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="ae1eb-142">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="ae1eb-142">Assembly manifest attributes</span></span>

<span data-ttu-id="ae1eb-143">Vous pouvez utiliser les attributs de manifeste de l’assembly pour fournir des informations dans le manifeste de l’assembly, y compris le titre, la description, l’alias par défaut et la configuration.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-143">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="ae1eb-144">Le tableau suivant décrit les attributs de manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-144">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="ae1eb-145">Attribut de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="ae1eb-145">Assembly manifest attribute</span></span>|<span data-ttu-id="ae1eb-146">Description</span><span class="sxs-lookup"><span data-stu-id="ae1eb-146">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="ae1eb-147">Valeur de chaîne désignant la configuration de l’assembly, comme Retail ou Debug.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-147">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="ae1eb-148">Le runtime n’utilise pas cette valeur.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-148">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="ae1eb-149">Valeur de chaîne qui spécifie un alias par défaut à utiliser en référençant les assemblys.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-149">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="ae1eb-150">Cette valeur fournit un nom convivial lorsque le nom de l’assembly ne l’est pas (comme une valeur GUID).</span><span class="sxs-lookup"><span data-stu-id="ae1eb-150">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="ae1eb-151">Cette valeur peut également être utilisée comme une forme abrégée du nom complet de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-151">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="ae1eb-152">Valeur de chaîne désignant une brève description qui résume la nature et l’objectif de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-152">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="ae1eb-153">Valeur de chaîne qui spécifie un nom convivial pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-153">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="ae1eb-154">Par exemple, un assembly nommé *comdlg* peut avoir le titre contrôle de boîte de dialogue commune Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-154">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="ae1eb-155">Attributs de nom fort</span><span class="sxs-lookup"><span data-stu-id="ae1eb-155">Strong name attributes</span></span>

<span data-ttu-id="ae1eb-156">Vous pouvez utiliser les attributs de nom fort pour définir un nom fort pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-156">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="ae1eb-157">Le tableau suivant décrit les attributs de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-157">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="ae1eb-158">Attribut Strong Name</span><span class="sxs-lookup"><span data-stu-id="ae1eb-158">Strong name attribute</span></span>|<span data-ttu-id="ae1eb-159">Description</span><span class="sxs-lookup"><span data-stu-id="ae1eb-159">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="ae1eb-160">Valeur booléenne qui indique que la signature différée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-160">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="ae1eb-161">Valeur de chaîne qui indique le nom du fichier contenant soit la clé publique (si la signature différée est utilisée), soit les clés publiques et privées transmises en tant que paramètres au constructeur de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-161">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="ae1eb-162">Notez que le nom de fichier est relatif au chemin d’accès du fichier de sortie ( *. exe* ou *. dll*), et non au chemin d’accès au fichier source.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-162">Note that the file name is relative to the output file path (the *.exe* or *.dll*), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="ae1eb-163">Indique le conteneur de clé qui possède la paire de clés transmise en tant que paramètre au constructeur de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-163">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="ae1eb-164">L’exemple de code suivant montre les attributs à appliquer lors de l’utilisation de la signature différée pour créer un assembly avec nom fort avec un fichier de clé publique appelé *myKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="ae1eb-164">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk*.</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a><span data-ttu-id="ae1eb-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae1eb-165">See also</span></span>

- [<span data-ttu-id="ae1eb-166">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="ae1eb-166">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="ae1eb-167">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="ae1eb-167">Program with assemblies</span></span>](program.md)
