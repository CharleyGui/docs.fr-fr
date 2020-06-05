---
title: Informations relatives à l'appelant
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 93fb1e327d65ac19f293a2f77b7d5712fc5e8d2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400666"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="7366f-102">Informations relatives à l’appelant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7366f-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="7366f-103">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="7366f-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="7366f-104">Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="7366f-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="7366f-105">Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="7366f-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="7366f-106">Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7366f-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="7366f-107">Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="7366f-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="7366f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7366f-108">Attribute</span></span>|<span data-ttu-id="7366f-109">Description</span><span class="sxs-lookup"><span data-stu-id="7366f-109">Description</span></span>|<span data-ttu-id="7366f-110">Type</span><span class="sxs-lookup"><span data-stu-id="7366f-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="7366f-111">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="7366f-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="7366f-112">C’est le chemin du fichier au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7366f-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="7366f-113">Numéro de ligne dans le fichier source dans lequel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="7366f-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="7366f-114">Méthode ou nom de la propriété de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="7366f-114">Method or property name of the caller.</span></span> <span data-ttu-id="7366f-115">Consultez [Noms de membres](#MEMBERNAMES), plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7366f-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="7366f-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="7366f-116">Example</span></span>  
 <span data-ttu-id="7366f-117">L'exemple suivant indique comment utiliser des attributs d'informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="7366f-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="7366f-118">À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.</span><span class="sxs-lookup"><span data-stu-id="7366f-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="7366f-119">Notes</span><span class="sxs-lookup"><span data-stu-id="7366f-119">Remarks</span></span>  
 <span data-ttu-id="7366f-120">Vous devez spécifier une valeur par défaut explicite pour chaque paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="7366f-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="7366f-121">Vous ne pouvez pas appliquer des attributs d'informations de l'appelant aux paramètres qui ne sont pas spécifiés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="7366f-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="7366f-122">Les attributs d'informations de l'appelant ne rendent pas un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="7366f-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="7366f-123">À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié.</span><span class="sxs-lookup"><span data-stu-id="7366f-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="7366f-124">Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7366f-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="7366f-125">Contrairement aux résultats de la propriété <xref:System.Exception.StackTrace%2A> pour les exceptions, les résultats ne sont pas affectés par l'obfuscation (protection de code).</span><span class="sxs-lookup"><span data-stu-id="7366f-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="7366f-126">Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="7366f-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="member-names"></a><a name="MEMBERNAMES"></a><span data-ttu-id="7366f-127">Noms de membres</span><span class="sxs-lookup"><span data-stu-id="7366f-127">Member Names</span></span>  
 <span data-ttu-id="7366f-128">Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="7366f-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="7366f-129">Vous évitez ainsi le problème que la **refactorisation de changement de nom** ne modifie pas les valeurs `String`.</span><span class="sxs-lookup"><span data-stu-id="7366f-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="7366f-130">Cet avantage est particulièrement utile pour les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="7366f-130">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="7366f-131">Utilisation du traçage et des programmes de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="7366f-131">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="7366f-132">Implémentation de l'interface <xref:System.ComponentModel.INotifyPropertyChanged> lors de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="7366f-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="7366f-133">Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="7366f-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="7366f-134">Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.</span><span class="sxs-lookup"><span data-stu-id="7366f-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="7366f-135">Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="7366f-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="7366f-136">Les appels se produisent à l'intérieur</span><span class="sxs-lookup"><span data-stu-id="7366f-136">Calls occurs within</span></span>|<span data-ttu-id="7366f-137">Résultat de nom de membre</span><span class="sxs-lookup"><span data-stu-id="7366f-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="7366f-138">Méthode, propriété ou événement</span><span class="sxs-lookup"><span data-stu-id="7366f-138">Method, property, or event</span></span>|<span data-ttu-id="7366f-139">Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.</span><span class="sxs-lookup"><span data-stu-id="7366f-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="7366f-140">Constructeur</span><span class="sxs-lookup"><span data-stu-id="7366f-140">Constructor</span></span>|<span data-ttu-id="7366f-141">La chaîne « .ctor »</span><span class="sxs-lookup"><span data-stu-id="7366f-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="7366f-142">Constructeur statique</span><span class="sxs-lookup"><span data-stu-id="7366f-142">Static constructor</span></span>|<span data-ttu-id="7366f-143">La chaîne « .cctor »</span><span class="sxs-lookup"><span data-stu-id="7366f-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="7366f-144">Destructeur</span><span class="sxs-lookup"><span data-stu-id="7366f-144">Destructor</span></span>|<span data-ttu-id="7366f-145">La chaîne « finalize »</span><span class="sxs-lookup"><span data-stu-id="7366f-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="7366f-146">Opérateurs définis par l'utilisateur ou conversions</span><span class="sxs-lookup"><span data-stu-id="7366f-146">User-defined operators or conversions</span></span>|<span data-ttu-id="7366f-147">Le nom généré pour le membre, par exemple, « op_Addition ».</span><span class="sxs-lookup"><span data-stu-id="7366f-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="7366f-148">Constructeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="7366f-148">Attribute constructor</span></span>|<span data-ttu-id="7366f-149">Le nom du membre auquel l'attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="7366f-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="7366f-150">Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.</span><span class="sxs-lookup"><span data-stu-id="7366f-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="7366f-151">Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)</span><span class="sxs-lookup"><span data-stu-id="7366f-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="7366f-152">Valeur par défaut du paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="7366f-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7366f-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7366f-153">See also</span></span>

- [<span data-ttu-id="7366f-154">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7366f-154">Attributes (Visual Basic)</span></span>](../../language-reference/attributes.md)
- [<span data-ttu-id="7366f-155">Attributs courants (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7366f-155">Common Attributes (Visual Basic)</span></span>](attributes/common-attributes.md)
- [<span data-ttu-id="7366f-156">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="7366f-156">Optional Parameters</span></span>](../language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="7366f-157">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7366f-157">Programming Concepts (Visual Basic)</span></span>](index.md)
