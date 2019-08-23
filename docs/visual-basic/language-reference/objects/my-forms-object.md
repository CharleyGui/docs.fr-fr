---
title: My. Forms, objet (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9fa5c77dd12c98100e3d17fc473a6802180d1e32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965979"
---
# <a name="myforms-object"></a><span data-ttu-id="e0165-102">My.Forms, objet</span><span class="sxs-lookup"><span data-stu-id="e0165-102">My.Forms Object</span></span>
<span data-ttu-id="e0165-103">Fournit des propriétés pour accéder à une instance de chaque Windows Form déclaré dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e0165-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0165-104">Notes</span><span class="sxs-lookup"><span data-stu-id="e0165-104">Remarks</span></span>  
 <span data-ttu-id="e0165-105">L' `My.Forms` objet fournit une instance de chaque formulaire dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e0165-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="e0165-106">Le nom de la propriété est le même que celui du formulaire auquel la propriété accède.</span><span class="sxs-lookup"><span data-stu-id="e0165-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="e0165-107">Vous pouvez accéder aux formulaires fournis par l' `My.Forms` objet à l’aide du nom du formulaire, sans qualification.</span><span class="sxs-lookup"><span data-stu-id="e0165-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="e0165-108">Étant donné que le nom de la propriété est le même que le nom du type du formulaire, cela vous permet d’accéder à un formulaire comme s’il avait une instance par défaut.</span><span class="sxs-lookup"><span data-stu-id="e0165-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="e0165-109">Par exemple, `My.Forms.Form1.Show` équivaut à `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="e0165-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="e0165-110">L' `My.Forms` objet expose uniquement les formulaires associés au projet actif.</span><span class="sxs-lookup"><span data-stu-id="e0165-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="e0165-111">Elle ne fournit pas l’accès aux formulaires déclarés dans les dll référencées.</span><span class="sxs-lookup"><span data-stu-id="e0165-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="e0165-112">Pour accéder à un formulaire fourni par une DLL, vous devez utiliser le nom qualifié du formulaire, écrit sous la forme *DllName*. *NomFormulaire*.</span><span class="sxs-lookup"><span data-stu-id="e0165-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="e0165-113">Vous pouvez utiliser la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriété pour obtenir une collection de tous les formulaires ouverts de l’application.</span><span class="sxs-lookup"><span data-stu-id="e0165-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="e0165-114">L’objet et ses propriétés sont uniquement disponibles pour les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="e0165-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e0165-115">Properties</span><span class="sxs-lookup"><span data-stu-id="e0165-115">Properties</span></span>  
 <span data-ttu-id="e0165-116">Chaque propriété de l' `My.Forms` objet permet d’accéder à une instance d’un formulaire dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e0165-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="e0165-117">Le nom de la propriété est le même que celui du formulaire auquel la propriété accède, et le type de propriété est le même que le type du formulaire.</span><span class="sxs-lookup"><span data-stu-id="e0165-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0165-118">En cas de collision de nom, le nom de la propriété permettant d’accéder à un formulaire est *RootNamespace*_*namespace*\_*NomFormulaire*.</span><span class="sxs-lookup"><span data-stu-id="e0165-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="e0165-119">Par exemple, considérez deux formulaires `Form1.`nommés si l’un de ces formulaires se trouve dans `WindowsApplication1` l’espace de noms `Namespace1`racine et dans l’espace de noms `My.Forms.WindowsApplication1_Namespace1_Form1`, vous accéderiez à ce formulaire via.</span><span class="sxs-lookup"><span data-stu-id="e0165-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="e0165-120">L' `My.Forms` objet fournit l’accès à l’instance du formulaire principal de l’application qui a été créée au démarrage.</span><span class="sxs-lookup"><span data-stu-id="e0165-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="e0165-121">Pour tous les autres formulaires, `My.Forms` l’objet crée une nouvelle instance du formulaire lors de son accès et le stocke.</span><span class="sxs-lookup"><span data-stu-id="e0165-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="e0165-122">Les tentatives suivantes d’accès à cette propriété retournent cette instance du formulaire.</span><span class="sxs-lookup"><span data-stu-id="e0165-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="e0165-123">Vous pouvez supprimer un formulaire en l’affectant `Nothing` à la propriété de ce formulaire.</span><span class="sxs-lookup"><span data-stu-id="e0165-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="e0165-124">L’accesseur Set de <xref:System.Windows.Forms.Form.Close%2A> propriété appelle la méthode du formulaire, puis `Nothing` assigne à la valeur stockée.</span><span class="sxs-lookup"><span data-stu-id="e0165-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="e0165-125">Si vous assignez une valeur `Nothing` autre que à la propriété, la méthode setter <xref:System.ArgumentException> lève une exception.</span><span class="sxs-lookup"><span data-stu-id="e0165-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="e0165-126">Vous pouvez tester si une propriété de l' `My.Forms` objet stocke une instance du formulaire à l’aide `Is` de `IsNot` l’opérateur or.</span><span class="sxs-lookup"><span data-stu-id="e0165-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="e0165-127">Vous pouvez utiliser ces opérateurs pour vérifier si la valeur de la propriété est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e0165-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0165-128">En règle générale `Is` , `IsNot` l’opérateur or doit lire la valeur de la propriété pour effectuer la comparaison.</span><span class="sxs-lookup"><span data-stu-id="e0165-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="e0165-129">Toutefois, si la propriété est actuellement `Nothing`stockée, la propriété crée une nouvelle instance du formulaire, puis retourne cette instance.</span><span class="sxs-lookup"><span data-stu-id="e0165-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="e0165-130">Toutefois, le compilateur Visual Basic traite différemment les propriétés de `My.Forms` l’objet et permet à `Is` l' `IsNot` opérateur ou de vérifier l’état de la propriété sans modifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="e0165-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0165-131">Exemples</span><span class="sxs-lookup"><span data-stu-id="e0165-131">Example</span></span>  
 <span data-ttu-id="e0165-132">Cet exemple modifie le titre du formulaire par `SidebarMenu` défaut.</span><span class="sxs-lookup"><span data-stu-id="e0165-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 <span data-ttu-id="e0165-133">Pour que cet exemple fonctionne, votre projet doit avoir un formulaire nommé `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="e0165-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="e0165-134">Ce code ne fonctionne que dans un projet d’application Windows.</span><span class="sxs-lookup"><span data-stu-id="e0165-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0165-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0165-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="e0165-136">Disponibilité par type de projet</span><span class="sxs-lookup"><span data-stu-id="e0165-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="e0165-137">Type de projet</span><span class="sxs-lookup"><span data-stu-id="e0165-137">Project type</span></span>|<span data-ttu-id="e0165-138">Disponible</span><span class="sxs-lookup"><span data-stu-id="e0165-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="e0165-139">Application Windows</span><span class="sxs-lookup"><span data-stu-id="e0165-139">Windows Application</span></span>|<span data-ttu-id="e0165-140">**Oui**</span><span class="sxs-lookup"><span data-stu-id="e0165-140">**Yes**</span></span>|  
|<span data-ttu-id="e0165-141">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="e0165-141">Class Library</span></span>|<span data-ttu-id="e0165-142">Non</span><span class="sxs-lookup"><span data-stu-id="e0165-142">No</span></span>|  
|<span data-ttu-id="e0165-143">Application console</span><span class="sxs-lookup"><span data-stu-id="e0165-143">Console Application</span></span>|<span data-ttu-id="e0165-144">Non</span><span class="sxs-lookup"><span data-stu-id="e0165-144">No</span></span>|  
|<span data-ttu-id="e0165-145">Bibliothèque de contrôles Windows</span><span class="sxs-lookup"><span data-stu-id="e0165-145">Windows Control Library</span></span>|<span data-ttu-id="e0165-146">Non</span><span class="sxs-lookup"><span data-stu-id="e0165-146">No</span></span>|  
|<span data-ttu-id="e0165-147">Bibliothèque de contrôles Web</span><span class="sxs-lookup"><span data-stu-id="e0165-147">Web Control Library</span></span>|<span data-ttu-id="e0165-148">Non</span><span class="sxs-lookup"><span data-stu-id="e0165-148">No</span></span>|  
|<span data-ttu-id="e0165-149">Service Windows</span><span class="sxs-lookup"><span data-stu-id="e0165-149">Windows Service</span></span>|<span data-ttu-id="e0165-150">Non</span><span class="sxs-lookup"><span data-stu-id="e0165-150">No</span></span>|  
|<span data-ttu-id="e0165-151">Site web</span><span class="sxs-lookup"><span data-stu-id="e0165-151">Web Site</span></span>|<span data-ttu-id="e0165-152">Non</span><span class="sxs-lookup"><span data-stu-id="e0165-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0165-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0165-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="e0165-154">Objects</span><span class="sxs-lookup"><span data-stu-id="e0165-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="e0165-155">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e0165-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="e0165-156">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e0165-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="e0165-157">Accès aux formulaires de l’application</span><span class="sxs-lookup"><span data-stu-id="e0165-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
