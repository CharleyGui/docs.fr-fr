---
title: 'Attributs réservés C : Suivi des informations sur les appelants'
ms.date: 04/09/2020
description: Ces attributs instruisent le compilateur de générer des informations sur le code qui appelle un membre. Vous utilisez le CallerFilePath, CallerLineNumber et CallerMemberName pour fournir des informations détaillées sur les traces
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389876"
---
# <a name="reserved-attributes-determine-caller-information"></a><span data-ttu-id="2a789-104">Attributs réservés : Déterminer les informations sur l’appelant</span><span class="sxs-lookup"><span data-stu-id="2a789-104">Reserved attributes: Determine caller information</span></span>

<span data-ttu-id="2a789-105">En utilisant des attributs d’information, vous obtenez des informations sur l’appelant à une méthode.</span><span class="sxs-lookup"><span data-stu-id="2a789-105">Using info attributes, you obtain information about the caller to a method.</span></span> <span data-ttu-id="2a789-106">Vous obtenez le chemin de fichier du code source, le numéro de ligne dans le code source et le nom du membre de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2a789-106">You obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="2a789-107">Pour obtenir des informations de membre de l’appelant, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="2a789-107">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="2a789-108">Chaque paramètre facultatif spécifie une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a789-108">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="2a789-109">Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="2a789-109">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="2a789-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a789-110">Attribute</span></span>|<span data-ttu-id="2a789-111">Description</span><span class="sxs-lookup"><span data-stu-id="2a789-111">Description</span></span>|<span data-ttu-id="2a789-112">Type</span><span class="sxs-lookup"><span data-stu-id="2a789-112">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="2a789-113">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2a789-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="2a789-114">Le chemin complet est le chemin au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2a789-114">The full path is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="2a789-115">Numéro de ligne dans le fichier source à partir duquel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="2a789-115">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="2a789-116">Nom de la méthode ou nom de la propriété de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2a789-116">Method name or property name of the caller.</span></span>|`String`|

<span data-ttu-id="2a789-117">Ces informations vous aident à écrire des traçages, à débogage et à créer des outils de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="2a789-117">This information helps you write tracing, debugging, and create diagnostic tools.</span></span> <span data-ttu-id="2a789-118">L’exemple suivant montre comment utiliser les attributs d’info de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2a789-118">The following example shows how to use caller info attributes.</span></span> <span data-ttu-id="2a789-119">À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.</span><span class="sxs-lookup"><span data-stu-id="2a789-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

<span data-ttu-id="2a789-120">Vous spécifiez une valeur par défaut explicite pour chaque paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="2a789-120">You specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="2a789-121">Vous ne pouvez pas appliquer des attributs d’information de l’appelant à des paramètres qui ne sont pas spécifiés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="2a789-121">You can't apply caller info attributes to parameters that aren't specified as optional.</span></span> <span data-ttu-id="2a789-122">Les attributs d’info de l’appelant ne rendent pas un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="2a789-122">The caller info attributes don't make a parameter optional.</span></span> <span data-ttu-id="2a789-123">À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié.</span><span class="sxs-lookup"><span data-stu-id="2a789-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span> <span data-ttu-id="2a789-124">Les valeurs d’info de l’appelant sont émises sous forme d’alphabétisés dans la langue intermédiaire (IL) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2a789-124">Caller info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="2a789-125">Contrairement aux résultats de la propriété <xref:System.Exception.StackTrace%2A> pour les exceptions, les résultats ne sont pas affectés par l'obfuscation (protection de code).</span><span class="sxs-lookup"><span data-stu-id="2a789-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span> <span data-ttu-id="2a789-126">Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="2a789-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="2a789-127">Noms de membres</span><span class="sxs-lookup"><span data-stu-id="2a789-127">Member names</span></span>

<span data-ttu-id="2a789-128">Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="2a789-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="2a789-129">Vous évitez ainsi le problème que la **refactorisation de changement de nom** ne modifie pas les valeurs `String`.</span><span class="sxs-lookup"><span data-stu-id="2a789-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="2a789-130">Cet avantage est particulièrement utile pour les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2a789-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="2a789-131">Utilisation du traçage et des programmes de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="2a789-131">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="2a789-132">Implémentation de l'interface <xref:System.ComponentModel.INotifyPropertyChanged> lors de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="2a789-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="2a789-133">Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="2a789-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="2a789-134">Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.</span><span class="sxs-lookup"><span data-stu-id="2a789-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="2a789-135">Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="2a789-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="2a789-136">Les appels se produisent à l’intérieur</span><span class="sxs-lookup"><span data-stu-id="2a789-136">Calls occur within</span></span>|<span data-ttu-id="2a789-137">Résultat de nom de membre</span><span class="sxs-lookup"><span data-stu-id="2a789-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="2a789-138">Méthode, propriété ou événement</span><span class="sxs-lookup"><span data-stu-id="2a789-138">Method, property, or event</span></span>|<span data-ttu-id="2a789-139">Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.</span><span class="sxs-lookup"><span data-stu-id="2a789-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="2a789-140">Constructeur</span><span class="sxs-lookup"><span data-stu-id="2a789-140">Constructor</span></span>|<span data-ttu-id="2a789-141">La chaîne « .ctor »</span><span class="sxs-lookup"><span data-stu-id="2a789-141">The string ".ctor"</span></span>|
|<span data-ttu-id="2a789-142">Constructeur statique</span><span class="sxs-lookup"><span data-stu-id="2a789-142">Static constructor</span></span>|<span data-ttu-id="2a789-143">La chaîne « .cctor »</span><span class="sxs-lookup"><span data-stu-id="2a789-143">The string ".cctor"</span></span>|
|<span data-ttu-id="2a789-144">Destructeur</span><span class="sxs-lookup"><span data-stu-id="2a789-144">Destructor</span></span>|<span data-ttu-id="2a789-145">La chaîne « finalize »</span><span class="sxs-lookup"><span data-stu-id="2a789-145">The string "Finalize"</span></span>|
|<span data-ttu-id="2a789-146">Opérateurs définis par l'utilisateur ou conversions</span><span class="sxs-lookup"><span data-stu-id="2a789-146">User-defined operators or conversions</span></span>|<span data-ttu-id="2a789-147">Le nom généré pour le membre, par exemple, « op_Addition ».</span><span class="sxs-lookup"><span data-stu-id="2a789-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="2a789-148">Constructeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="2a789-148">Attribute constructor</span></span>|<span data-ttu-id="2a789-149">Le nom de la méthode ou de la propriété à laquelle s’applique l'attribut.</span><span class="sxs-lookup"><span data-stu-id="2a789-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="2a789-150">Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.</span><span class="sxs-lookup"><span data-stu-id="2a789-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="2a789-151">Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)</span><span class="sxs-lookup"><span data-stu-id="2a789-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="2a789-152">Valeur par défaut du paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="2a789-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2a789-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a789-153">See also</span></span>

- [<span data-ttu-id="2a789-154">Arguments nommés et facultatifs</span><span class="sxs-lookup"><span data-stu-id="2a789-154">Named and Optional Arguments</span></span>](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="2a789-155">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a789-155">Attributes</span></span>](../../../standard/attributes/index.md)
