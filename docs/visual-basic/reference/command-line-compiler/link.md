---
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 6082806591d398aa8b16b44e769a3f8078ce62d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387736"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="40a1f-102">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40a1f-102">-link (Visual Basic)</span></span>
<span data-ttu-id="40a1f-103">Fait que le compilateur rend disponible pour le projet en cours de compilation les informations de type COM des assemblys spécifiés.</span><span class="sxs-lookup"><span data-stu-id="40a1f-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40a1f-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="40a1f-105">ou</span><span class="sxs-lookup"><span data-stu-id="40a1f-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="40a1f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="40a1f-106">Arguments</span></span>  
  
|<span data-ttu-id="40a1f-107">Terme</span><span class="sxs-lookup"><span data-stu-id="40a1f-107">Term</span></span>|<span data-ttu-id="40a1f-108">Définition</span><span class="sxs-lookup"><span data-stu-id="40a1f-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="40a1f-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="40a1f-109">Required.</span></span> <span data-ttu-id="40a1f-110">Liste délimitée par des virgules des noms de fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="40a1f-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="40a1f-111">Si le nom de fichier contient un espace, placez-le entre des guillemets.</span><span class="sxs-lookup"><span data-stu-id="40a1f-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40a1f-112">Notes</span><span class="sxs-lookup"><span data-stu-id="40a1f-112">Remarks</span></span>  
 <span data-ttu-id="40a1f-113">L’option `-link` vous permet de déployer une application qui a des informations de type incorporées.</span><span class="sxs-lookup"><span data-stu-id="40a1f-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="40a1f-114">L’application peut ensuite utiliser des types dans un assembly de runtime qui implémentent les informations de type incorporées sans nécessiter une référence à l’assembly de runtime.</span><span class="sxs-lookup"><span data-stu-id="40a1f-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="40a1f-115">Si différentes versions de l’assembly de runtime sont publiées, l’application qui contient les informations de type incorporées peut fonctionner avec les différentes versions sans devoir être recompilée.</span><span class="sxs-lookup"><span data-stu-id="40a1f-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="40a1f-116">Pour un exemple, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="40a1f-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="40a1f-117">L’utilisation de l’option `-link` est particulièrement utile quand vous travaillez avec COM Interop.</span><span class="sxs-lookup"><span data-stu-id="40a1f-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="40a1f-118">Vous pouvez incorporer des types COM afin que votre application ne nécessite plus un assembly PIA (Primary Interop Assembly) sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="40a1f-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="40a1f-119">L’option `-link` indique au compilateur d’incorporer les informations de type COM provenant de l’assembly Interop référencé dans le code compilé résultant.</span><span class="sxs-lookup"><span data-stu-id="40a1f-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="40a1f-120">Le type COM est identifié par la valeur du CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="40a1f-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="40a1f-121">Par conséquent, votre application peut s’exécuter sur un ordinateur cible où les mêmes types COM ont été installés avec les mêmes valeurs de CLSID.</span><span class="sxs-lookup"><span data-stu-id="40a1f-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="40a1f-122">Les applications qui automatisent Microsoft Office sont un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="40a1f-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="40a1f-123">Étant donné que les applications comme Office gardent habituellement la même valeur de CLSID à travers différentes versions, votre application peut utiliser les types COM référencés dès lors que le .NET Framework 4 ou ultérieur est installé sur l’ordinateur cible, et que votre application utilise les méthodes, propriétés ou événements qui sont inclus dans les types COM référencés.</span><span class="sxs-lookup"><span data-stu-id="40a1f-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="40a1f-124">L’option `-link` incorpore seulement les interfaces, les structures et les délégués.</span><span class="sxs-lookup"><span data-stu-id="40a1f-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="40a1f-125">L’incorporation de classes COM n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="40a1f-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40a1f-126">Quand vous créez une instance d’un type COM incorporé dans votre code, vous devez créer l’instance à l’aide de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="40a1f-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="40a1f-127">Une tentative de création d’une instance d’un type COM incorporé à l’aide de la coclasse provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="40a1f-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="40a1f-128">Pour définir l’option `-link` dans Visual Studio, ajoutez une référence d’assembly et définissez la propriété `Embed Interop Types` sur **true**.</span><span class="sxs-lookup"><span data-stu-id="40a1f-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="40a1f-129">La valeur par défaut pour la propriété `Embed Interop Types` est **false**.</span><span class="sxs-lookup"><span data-stu-id="40a1f-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="40a1f-130">Si vous liez à un assembly COM (Assembly A) qui référence lui-même un autre assembly COM (Assembly B), vous devez également lier à l’Assembly B si une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="40a1f-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="40a1f-131">Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="40a1f-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="40a1f-132">Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.</span><span class="sxs-lookup"><span data-stu-id="40a1f-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="40a1f-133">Utilisez [-LIBPATH](libpath.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="40a1f-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="40a1f-134">À l’instar de l’option [de compilateur-Reference](reference.md) , l' `-link` option de compilateur utilise le fichier réponse Vbc. rsp, qui référence les assemblys .NET Framework fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="40a1f-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="40a1f-135">Utilisez l’option [de compilateur-noconfig](noconfig.md) si vous ne souhaitez pas que le compilateur utilise le fichier Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="40a1f-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="40a1f-136">La forme abrégée de `-link` est `-l`.</span><span class="sxs-lookup"><span data-stu-id="40a1f-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="40a1f-137">Types génériques et imbriqués</span><span class="sxs-lookup"><span data-stu-id="40a1f-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="40a1f-138">Les sections suivantes décrivent les limitations de l’utilisation de types génériques dans les applications qui incorporent des types interop.</span><span class="sxs-lookup"><span data-stu-id="40a1f-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="40a1f-139">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="40a1f-139">Generic Interfaces</span></span>  
 <span data-ttu-id="40a1f-140">Vous ne pouvez pas utiliser des interfaces génériques incorporées depuis un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="40a1f-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="40a1f-141">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="40a1f-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="40a1f-142">Types ayant des paramètres génériques</span><span class="sxs-lookup"><span data-stu-id="40a1f-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="40a1f-143">Vous ne pouvez pas utiliser des types qui ont un paramètre générique dont le type est incorporé depuis un assembly d’interopérabilité si ce type provient d’un assembly externe.</span><span class="sxs-lookup"><span data-stu-id="40a1f-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="40a1f-144">Cette restriction ne s’applique pas aux interfaces.</span><span class="sxs-lookup"><span data-stu-id="40a1f-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="40a1f-145">Prenons l’exemple de l’interface <xref:Microsoft.Office.Interop.Excel.Range> qui est définie dans l’assembly <xref:Microsoft.Office.Interop.Excel>.</span><span class="sxs-lookup"><span data-stu-id="40a1f-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="40a1f-146">Si une bibliothèque incorpore les types interop de l’assembly <xref:Microsoft.Office.Interop.Excel> et expose une méthode qui retourne un type générique qui a un paramètre dont le type est l’interface <xref:Microsoft.Office.Interop.Excel.Range>, cette méthode doit retourner une interface générique, comme dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="40a1f-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="40a1f-147">Dans l’exemple suivant, le code client peut appeler la méthode qui retourne l’interface générique <xref:System.Collections.IList> sans erreur.</span><span class="sxs-lookup"><span data-stu-id="40a1f-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="40a1f-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="40a1f-148">Example</span></span>  
 <span data-ttu-id="40a1f-149">La ligne de commande suivante compile le fichier source `OfficeApp.vb` et les assemblys de référence à partir de `COMData1.dll` et `COMData2.dll` à produire `OfficeApp.exe` .</span><span class="sxs-lookup"><span data-stu-id="40a1f-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="40a1f-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40a1f-150">See also</span></span>

- [<span data-ttu-id="40a1f-151">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40a1f-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="40a1f-152">Procédure pas à pas : incorporation de types provenant d’assemblys managés</span><span class="sxs-lookup"><span data-stu-id="40a1f-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="40a1f-153">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40a1f-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="40a1f-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="40a1f-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="40a1f-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="40a1f-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="40a1f-156">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="40a1f-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="40a1f-157">Présentation de COM Interop</span><span class="sxs-lookup"><span data-stu-id="40a1f-157">Introduction to COM Interop</span></span>](../../programming-guide/com-interop/introduction-to-com-interop.md)
