---
description: -link (Options du compilateur C#)
title: -link (Options du compilateur C#)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 6fd291c49c282713ea56ca20d8d58616d38ec752
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465713"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="9f808-103">-link (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9f808-103">-link (C# Compiler Options)</span></span>
<span data-ttu-id="9f808-104">Fait que le compilateur rend disponible pour le projet en cours de compilation les informations de type COM des assemblys spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9f808-104">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f808-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f808-105">Syntax</span></span>

```console
-link:fileList
// -or-
-l:fileList
```

## <a name="arguments"></a><span data-ttu-id="9f808-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f808-106">Arguments</span></span>
 `fileList`  
 <span data-ttu-id="9f808-107">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9f808-107">Required.</span></span> <span data-ttu-id="9f808-108">Liste délimitée par des virgules des noms de fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9f808-108">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="9f808-109">Si le nom de fichier contient un espace, placez-le entre des guillemets.</span><span class="sxs-lookup"><span data-stu-id="9f808-109">If the file name contains a space, enclose the name in quotation marks.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f808-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="9f808-110">Remarks</span></span>
 <span data-ttu-id="9f808-111">L’option `-link` vous permet de déployer une application qui a des informations de type incorporées.</span><span class="sxs-lookup"><span data-stu-id="9f808-111">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="9f808-112">L’application peut ensuite utiliser des types dans un assembly de runtime qui implémentent les informations de type incorporées sans nécessiter une référence à l’assembly de runtime.</span><span class="sxs-lookup"><span data-stu-id="9f808-112">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="9f808-113">Si différentes versions de l’assembly de runtime sont publiées, l’application qui contient les informations de type incorporées peut fonctionner avec les différentes versions sans devoir être recompilée.</span><span class="sxs-lookup"><span data-stu-id="9f808-113">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="9f808-114">Pour un exemple, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9f808-114">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="9f808-115">L’utilisation de l’option `-link` est particulièrement utile quand vous travaillez avec COM Interop.</span><span class="sxs-lookup"><span data-stu-id="9f808-115">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="9f808-116">Vous pouvez incorporer des types COM afin que votre application ne nécessite plus un assembly PIA (Primary Interop Assembly) sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="9f808-116">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="9f808-117">L’option `-link` indique au compilateur d’incorporer les informations de type COM provenant de l’assembly Interop référencé dans le code compilé résultant.</span><span class="sxs-lookup"><span data-stu-id="9f808-117">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="9f808-118">Le type COM est identifié par la valeur du CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="9f808-118">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="9f808-119">Par conséquent, votre application peut s’exécuter sur un ordinateur cible où les mêmes types COM ont été installés avec les mêmes valeurs de CLSID.</span><span class="sxs-lookup"><span data-stu-id="9f808-119">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="9f808-120">Les applications qui automatisent Microsoft Office sont un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="9f808-120">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="9f808-121">Étant donné que les applications comme Office gardent habituellement la même valeur de CLSID à travers différentes versions, votre application peut utiliser les types COM référencés dès lors que le .NET Framework 4 ou ultérieur est installé sur l’ordinateur cible, et que votre application utilise les méthodes, propriétés ou événements qui sont inclus dans les types COM référencés.</span><span class="sxs-lookup"><span data-stu-id="9f808-121">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>

 <span data-ttu-id="9f808-122">L’option `-link` incorpore seulement les interfaces, les structures et les délégués.</span><span class="sxs-lookup"><span data-stu-id="9f808-122">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="9f808-123">L’incorporation de classes COM n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="9f808-123">Embedding COM classes is not supported.</span></span>

> [!NOTE]
> <span data-ttu-id="9f808-124">Quand vous créez une instance d’un type COM incorporé dans votre code, vous devez créer l’instance à l’aide de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="9f808-124">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="9f808-125">Une tentative de création d’une instance d’un type COM incorporé à l’aide de la coclasse provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="9f808-125">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>

 <span data-ttu-id="9f808-126">Pour définir l’option `-link` dans Visual Studio, ajoutez une référence d’assembly et définissez la propriété `Embed Interop Types` sur **true**.</span><span class="sxs-lookup"><span data-stu-id="9f808-126">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="9f808-127">La valeur par défaut pour la propriété `Embed Interop Types` est **false**.</span><span class="sxs-lookup"><span data-stu-id="9f808-127">The default for the `Embed Interop Types` property is **false**.</span></span>

 <span data-ttu-id="9f808-128">Si vous liez à un assembly COM (Assembly A) qui référence lui-même un autre assembly COM (Assembly B), vous devez également lier à l’Assembly B si une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="9f808-128">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>

- <span data-ttu-id="9f808-129">Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="9f808-129">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>

- <span data-ttu-id="9f808-130">Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.</span><span class="sxs-lookup"><span data-stu-id="9f808-130">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>

 <span data-ttu-id="9f808-131">À l’instar de l’option [-Reference](./reference-compiler-option.md) du compilateur, l' `-link` option du compilateur utilise le fichier réponse CSC. rsp, qui référence les assemblys .net fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="9f808-131">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET assemblies.</span></span> <span data-ttu-id="9f808-132">Utilisez l’option [-noconfig](./noconfig-compiler-option.md) du compilateur si vous ne voulez pas que le compilateur utilise le fichier Csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="9f808-132">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>

 <span data-ttu-id="9f808-133">La forme abrégée de `-link` est `-l`.</span><span class="sxs-lookup"><span data-stu-id="9f808-133">The short form of `-link` is `-l`.</span></span>

## <a name="generics-and-embedded-types"></a><span data-ttu-id="9f808-134">Types génériques et imbriqués</span><span class="sxs-lookup"><span data-stu-id="9f808-134">Generics and Embedded Types</span></span>
 <span data-ttu-id="9f808-135">Les sections suivantes décrivent les limitations de l’utilisation de types génériques dans les applications qui incorporent des types interop.</span><span class="sxs-lookup"><span data-stu-id="9f808-135">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>

### <a name="generic-interfaces"></a><span data-ttu-id="9f808-136">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="9f808-136">Generic Interfaces</span></span>
 <span data-ttu-id="9f808-137">Vous ne pouvez pas utiliser des interfaces génériques incorporées depuis un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="9f808-137">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="9f808-138">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9f808-138">This is shown in the following example.</span></span>

 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]

### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="9f808-139">Types ayant des paramètres génériques</span><span class="sxs-lookup"><span data-stu-id="9f808-139">Types That Have Generic Parameters</span></span>
 <span data-ttu-id="9f808-140">Vous ne pouvez pas utiliser des types qui ont un paramètre générique dont le type est incorporé depuis un assembly d’interopérabilité si ce type provient d’un assembly externe.</span><span class="sxs-lookup"><span data-stu-id="9f808-140">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="9f808-141">Cette restriction ne s’applique pas aux interfaces.</span><span class="sxs-lookup"><span data-stu-id="9f808-141">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="9f808-142">Prenons l’exemple de l’interface <xref:Microsoft.Office.Interop.Excel.Range> qui est définie dans l’assembly <xref:Microsoft.Office.Interop.Excel>.</span><span class="sxs-lookup"><span data-stu-id="9f808-142">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="9f808-143">Si une bibliothèque incorpore les types interop de l’assembly <xref:Microsoft.Office.Interop.Excel> et expose une méthode qui retourne un type générique qui a un paramètre dont le type est l’interface <xref:Microsoft.Office.Interop.Excel.Range>, cette méthode doit retourner une interface générique, comme dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="9f808-143">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>

[!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs)]

 <span data-ttu-id="9f808-144">Dans l’exemple suivant, le code client peut appeler la méthode qui retourne l’interface générique <xref:System.Collections.IList> sans erreur.</span><span class="sxs-lookup"><span data-stu-id="9f808-144">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>

 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]

## <a name="example"></a><span data-ttu-id="9f808-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="9f808-145">Example</span></span>
 <span data-ttu-id="9f808-146">Le code suivant compile le fichier source `OfficeApp.cs` et des assemblys de référence à partir de `COMData1.dll` et de `COMData2.dll` pour produire `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="9f808-146">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>

```csharp
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs
```

## <a name="see-also"></a><span data-ttu-id="9f808-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f808-147">See also</span></span>

- [<span data-ttu-id="9f808-148">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="9f808-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9f808-149">Procédure pas à pas : incorporation de types provenant d’assemblys managés</span><span class="sxs-lookup"><span data-stu-id="9f808-149">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="9f808-150">-Reference (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9f808-150">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="9f808-151">-noconfig (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9f808-151">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="9f808-152">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="9f808-152">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="9f808-153">Vue d'ensemble de l'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="9f808-153">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
