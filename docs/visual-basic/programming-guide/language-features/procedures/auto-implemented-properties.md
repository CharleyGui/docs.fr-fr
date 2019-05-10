---
title: Propriétés implémentées automatiquement (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: 4577609c78271ac91e011b20ef6a8b4066072428
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649664"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="c85a0-102">Propriétés implémentées automatiquement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c85a0-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="c85a0-103">*Propriétés implémentées automatiquement* vous permettent de spécifier rapidement une propriété d’une classe sans avoir à écrire du code pour `Get` et `Set` la propriété.</span><span class="sxs-lookup"><span data-stu-id="c85a0-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="c85a0-104">Quand vous écrivez du code pour une propriété implémentée automatiquement, le compilateur Visual Basic crée automatiquement un champ privé pour stocker la variable de propriété en plus de créer les procédures `Get` et `Set` associées.</span><span class="sxs-lookup"><span data-stu-id="c85a0-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="c85a0-105">Avec les propriétés implémentées automatiquement, une propriété, y compris une valeur par défaut, peut être déclarée en une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="c85a0-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="c85a0-106">L'exemple suivant montre trois déclarations de propriété.</span><span class="sxs-lookup"><span data-stu-id="c85a0-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="c85a0-107">Une propriété implémentée automatiquement est équivalente à une propriété dont la valeur de propriété est stockée dans un champ privé.</span><span class="sxs-lookup"><span data-stu-id="c85a0-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="c85a0-108">L'exemple de code suivant montre une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c85a0-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="c85a0-109">L'exemple de code suivant montre le code équivalent pour l'exemple précédent de propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c85a0-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="c85a0-110">Le code suivant montre l'implémentation des propriétés en lecture seule :</span><span class="sxs-lookup"><span data-stu-id="c85a0-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="c85a0-111">Vous pouvez assigner la propriété avec des expressions d'initialisation, comme illustré dans cet exemple, ou vous pouvez assigner les propriétés dans le constructeur du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="c85a0-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="c85a0-112">Vous pouvez assigner les champs de stockage des propriétés en lecture seule à tout moment.</span><span class="sxs-lookup"><span data-stu-id="c85a0-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="c85a0-113">Champ de stockage</span><span class="sxs-lookup"><span data-stu-id="c85a0-113">Backing Field</span></span>  
 <span data-ttu-id="c85a0-114">Lorsque vous déclarez une propriété implémentée automatiquement, Visual Basic crée automatiquement un champ privé masqué appelé le *champ de stockage* pour contenir la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="c85a0-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="c85a0-115">Le nom du champ de stockage correspond au nom de la propriété implémentée automatiquement précédé d'un trait de soulignement (_).</span><span class="sxs-lookup"><span data-stu-id="c85a0-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="c85a0-116">Par exemple, si vous déclarez une propriété implémentée automatiquement nommée `ID`, le champ de stockage est nommé `_ID`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="c85a0-117">Si vous incluez un membre de votre classe également nommé `_ID`, vous créez un conflit de noms et Visual Basic signale une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="c85a0-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="c85a0-118">Le champ de stockage possède également les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c85a0-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="c85a0-119">Le modificateur d'accès pour le champ de stockage est toujours `Private`, même quand la propriété a elle-même un niveau d'accès différent, tel que `Public`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="c85a0-120">Si la propriété est marquée comme `Shared`, le champ de stockage est également partagé.</span><span class="sxs-lookup"><span data-stu-id="c85a0-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="c85a0-121">Les attributs spécifiés pour la propriété ne s'appliquent pas au champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="c85a0-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="c85a0-122">Le champ de stockage est accessible à partir du code dans la classe et des outils de débogage tels que la fenêtre Espion.</span><span class="sxs-lookup"><span data-stu-id="c85a0-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="c85a0-123">Toutefois, le champ de stockage ne s'affiche pas dans une liste de saisie semi-automatique IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c85a0-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="c85a0-124">Initialisation d'une propriété implémentée automatiquement</span><span class="sxs-lookup"><span data-stu-id="c85a0-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="c85a0-125">Toute expression pouvant être utilisée pour initialiser un champ est valide pour l'initialisation d'une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c85a0-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="c85a0-126">Quand vous initialisez une propriété implémentée automatiquement, l'expression est évaluée et passée à la procédure `Set` pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="c85a0-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="c85a0-127">Les exemples de code suivants montrent certaines propriétés implémentées automatiquement qui incluent des valeurs initiales.</span><span class="sxs-lookup"><span data-stu-id="c85a0-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="c85a0-128">Vous ne pouvez pas initialiser une propriété implémentée automatiquement qui est membre d'une `Interface` ou qui est marquée `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="c85a0-129">Quand vous déclarez une propriété implémentée automatiquement en tant que membre d'une `Structure`, vous pouvez initialiser la propriété implémentée automatiquement seulement si elle est marquée `Shared`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="c85a0-130">Quand vous déclarez une propriété implémentée automatiquement en tant que tableau, vous ne pouvez pas spécifier des limites d'index de tableau explicites.</span><span class="sxs-lookup"><span data-stu-id="c85a0-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="c85a0-131">Toutefois, vous pouvez fournir une valeur à l'aide d'un initialiseur de tableau, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="c85a0-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="c85a0-132">Définitions de propriétés qui requièrent la syntaxe standard</span><span class="sxs-lookup"><span data-stu-id="c85a0-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="c85a0-133">Les propriétés implémentées automatiquement sont pratiques et prennent en charge de nombreux scénarios de programmation.</span><span class="sxs-lookup"><span data-stu-id="c85a0-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="c85a0-134">Toutefois, il existe des situations dans lesquelles vous ne pouvez pas utiliser une propriété implémentée automatiquement et devez utiliser à la place de standard, ou *développé*, syntaxe de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c85a0-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="c85a0-135">Vous devez utiliser la syntaxe de définition de propriété développée pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c85a0-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="c85a0-136">Ajouter du code à la procédure `Get` ou `Set` d'une propriété, tel que du code permettant de valider des valeurs entrantes dans la procédure `Set`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="c85a0-137">Par exemple, vous pouvez vérifier qu'une chaîne représentant un numéro de téléphone contient le nombre de chiffres requis avant de définir la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c85a0-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="c85a0-138">Spécifier une accessibilité différente pour les procédures `Get` et `Set`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="c85a0-139">Par exemple, vous souhaiterez peut-être définir la procédure `Set` comme `Private` et la procédure `Get` comme `Public`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="c85a0-140">Créer des propriétés `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="c85a0-141">Utiliser des propriétés paramétrables (notamment les propriétés `Default`).</span><span class="sxs-lookup"><span data-stu-id="c85a0-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="c85a0-142">Vous devez déclarer une propriété développée pour pouvoir spécifier un paramètre pour la propriété, ou pour spécifier des paramètres supplémentaires pour la procédure `Set`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="c85a0-143">Placer un attribut sur le champ de stockage ou modifier le niveau d'accès du champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="c85a0-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="c85a0-144">Fournir des commentaires XML pour le champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="c85a0-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="c85a0-145">Développement d’une propriété implémentée automatiquement</span><span class="sxs-lookup"><span data-stu-id="c85a0-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="c85a0-146">Si vous devez convertir une propriété implémentée automatiquement en une propriété développée qui contient une procédure `Get` ou `Set`, l’éditeur de code de Visual Basic peut générer automatiquement les procédures `Get` et `Set`, et l’instruction `End Property` pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="c85a0-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="c85a0-147">Le code est généré si vous placez le curseur sur une ligne vierge suivant le `Property` instruction, tapez un `G` (pour `Get`) ou un `S` (pour `Set`) et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c85a0-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="c85a0-148">L'éditeur de code de Visual Basic génère automatiquement la procédure `Get` ou `Set` pour les propriétés en lecture seule et en écriture seule quand vous appuyez sur Entrée à la fin d'une instruction `Property`.</span><span class="sxs-lookup"><span data-stu-id="c85a0-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c85a0-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c85a0-149">See also</span></span>

- [<span data-ttu-id="c85a0-150">Guide pratique pour Déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c85a0-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="c85a0-151">Guide pratique pour Déclarer une propriété avec des niveaux d’accès mixtes</span><span class="sxs-lookup"><span data-stu-id="c85a0-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="c85a0-152">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="c85a0-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="c85a0-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c85a0-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="c85a0-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="c85a0-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="c85a0-155">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="c85a0-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
