---
title: Informations sur l’appelant
description: Décrit comment utiliser les attributs d’argument d’informations de l’appelant pour obtenir des informations d’appelant à partir d’une méthode.
ms.date: 04/25/2017
ms.openlocfilehash: e7bbc3830a95bd25cfc2fb369b204d367b775815
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106580"
---
# <a name="caller-information"></a><span data-ttu-id="e7ca2-103">Informations sur l’appelant</span><span class="sxs-lookup"><span data-stu-id="e7ca2-103">Caller information</span></span>

<span data-ttu-id="e7ca2-104">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="e7ca2-105">Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="e7ca2-106">Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="e7ca2-107">Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="e7ca2-108">Le tableau suivant répertorie les attributs d’informations de l’appelant qui sont définis dans l’espace de noms [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) :</span><span class="sxs-lookup"><span data-stu-id="e7ca2-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="e7ca2-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7ca2-109">Attribute</span></span>|<span data-ttu-id="e7ca2-110">Description</span><span class="sxs-lookup"><span data-stu-id="e7ca2-110">Description</span></span>|<span data-ttu-id="e7ca2-111">Type</span><span class="sxs-lookup"><span data-stu-id="e7ca2-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="e7ca2-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="e7ca2-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="e7ca2-113">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="e7ca2-114">C’est le chemin d’accès au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="e7ca2-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="e7ca2-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="e7ca2-116">Numéro de ligne dans le fichier source dans lequel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="e7ca2-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="e7ca2-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="e7ca2-118">Méthode ou nom de la propriété de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-118">Method or property name of the caller.</span></span> <span data-ttu-id="e7ca2-119">Consultez la section noms de membres plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="e7ca2-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7ca2-120">Example</span></span>

<span data-ttu-id="e7ca2-121">L’exemple suivant montre comment vous pouvez utiliser ces attributs pour suivre un appelant.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a><span data-ttu-id="e7ca2-122">Notes</span><span class="sxs-lookup"><span data-stu-id="e7ca2-122">Remarks</span></span>

<span data-ttu-id="e7ca2-123">Les attributs d’informations de l’appelant ne peuvent être appliqués qu’à des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="e7ca2-124">Les attributs d’informations de l’appelant forcent le compilateur à écrire la valeur appropriée pour chaque paramètre facultatif décoré avec un attribut d’informations de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-124">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="e7ca2-125">Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="e7ca2-126">Contrairement aux résultats de la propriété [StackTrace](/dotnet/api/system.diagnostics.stacktrace) pour les exceptions, les résultats ne sont pas affectés par l’obscurcissement.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-126">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="e7ca2-127">Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="e7ca2-128">Noms de membres</span><span class="sxs-lookup"><span data-stu-id="e7ca2-128">Member names</span></span>

<span data-ttu-id="e7ca2-129">Vous pouvez utiliser l' [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribut pour éviter de spécifier le nom de membre `String` en tant qu’argument de la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-129">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="e7ca2-130">Grâce à cette technique, vous évitez le problème que la refactorisation de changement de nom `String` ne modifie pas les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-130">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="e7ca2-131">Cet avantage est particulièrement utile pour les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7ca2-131">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="e7ca2-132">Utilisation du traçage et des programmes de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-132">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="e7ca2-133">Implémentation de l’interface [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) lors de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-133">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="e7ca2-134">Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="e7ca2-135">Sans l' [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribut, vous devez spécifier le nom de la propriété en tant que littéral.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-135">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="e7ca2-136">Le graphique suivant montre les noms de membres qui sont retournés lorsque vous utilisez l’attribut CallerMemberName.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-136">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="e7ca2-137">Les appels se produisent à l'intérieur</span><span class="sxs-lookup"><span data-stu-id="e7ca2-137">Calls occurs within</span></span>|<span data-ttu-id="e7ca2-138">Résultat de nom de membre</span><span class="sxs-lookup"><span data-stu-id="e7ca2-138">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="e7ca2-139">Méthode, propriété ou événement</span><span class="sxs-lookup"><span data-stu-id="e7ca2-139">Method, property, or event</span></span>|<span data-ttu-id="e7ca2-140">Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-140">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="e7ca2-141">Constructeur</span><span class="sxs-lookup"><span data-stu-id="e7ca2-141">Constructor</span></span>|<span data-ttu-id="e7ca2-142">La chaîne « .ctor »</span><span class="sxs-lookup"><span data-stu-id="e7ca2-142">The string ".ctor"</span></span>|
|<span data-ttu-id="e7ca2-143">Constructeur statique</span><span class="sxs-lookup"><span data-stu-id="e7ca2-143">Static constructor</span></span>|<span data-ttu-id="e7ca2-144">La chaîne « .cctor »</span><span class="sxs-lookup"><span data-stu-id="e7ca2-144">The string ".cctor"</span></span>|
|<span data-ttu-id="e7ca2-145">Destructeur</span><span class="sxs-lookup"><span data-stu-id="e7ca2-145">Destructor</span></span>|<span data-ttu-id="e7ca2-146">La chaîne « finalize »</span><span class="sxs-lookup"><span data-stu-id="e7ca2-146">The string "Finalize"</span></span>|
|<span data-ttu-id="e7ca2-147">Opérateurs définis par l'utilisateur ou conversions</span><span class="sxs-lookup"><span data-stu-id="e7ca2-147">User-defined operators or conversions</span></span>|<span data-ttu-id="e7ca2-148">Le nom généré pour le membre, par exemple, « op_Addition ».</span><span class="sxs-lookup"><span data-stu-id="e7ca2-148">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="e7ca2-149">Constructeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="e7ca2-149">Attribute constructor</span></span>|<span data-ttu-id="e7ca2-150">Le nom du membre auquel l'attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="e7ca2-151">Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="e7ca2-152">Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)</span><span class="sxs-lookup"><span data-stu-id="e7ca2-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="e7ca2-153">Valeur par défaut du paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-153">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e7ca2-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7ca2-154">See also</span></span>

- [<span data-ttu-id="e7ca2-155">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7ca2-155">Attributes</span></span>](attributes.md)
- [<span data-ttu-id="e7ca2-156">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="e7ca2-156">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)
- [<span data-ttu-id="e7ca2-157">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="e7ca2-157">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)
