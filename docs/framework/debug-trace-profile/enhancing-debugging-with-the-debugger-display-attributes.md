---
title: Amélioration du débogage avec les attributs d'affichage de débogueur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
ms.openlocfilehash: ca118bffb045a0e7e3a5084916a0ff8020ebda90
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216494"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="eb049-102">Amélioration du débogage avec les attributs d'affichage de débogueur</span><span class="sxs-lookup"><span data-stu-id="eb049-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="eb049-103">Les attributs d’affichage de débogueur permettent au développeur du type, qui spécifie et appréhende le mieux le comportement d’exécution de ce type, de spécifier également ce à quoi le type ressemblera une fois affiché dans un débogueur.</span><span class="sxs-lookup"><span data-stu-id="eb049-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="eb049-104">De plus, les attributs d’affichage de débogueur qui fournissent une propriété `Target` peuvent être appliqués au niveau de l’assembly par des utilisateurs sans qu’il leur soit nécessaire de connaître le code source.</span><span class="sxs-lookup"><span data-stu-id="eb049-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="eb049-105">L’attribut <xref:System.Diagnostics.DebuggerDisplayAttribute> contrôle la façon dont un type ou un membre s’affiche dans les fenêtres de variables du débogueur.</span><span class="sxs-lookup"><span data-stu-id="eb049-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="eb049-106">L’attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> contrôle si une classe ou un champ s’affiche dans les fenêtres de variables du débogueur et comment ils s’affichent.</span><span class="sxs-lookup"><span data-stu-id="eb049-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="eb049-107">L’attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> spécifie un type de substitution (ou un proxy) pour un type, et modifie le mode d’affichage de ce type dans les fenêtres de débogage.</span><span class="sxs-lookup"><span data-stu-id="eb049-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="eb049-108">Lorsque vous affichez une variable qui a un proxy, ou type de substitution, le proxy est intégré au type d’origine dans la fenêtre d’affichage du débogueur.</span><span class="sxs-lookup"><span data-stu-id="eb049-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="eb049-109">La fenêtre de variables du débogueur   n'affiche que les membres publics du type du proxy.</span><span class="sxs-lookup"><span data-stu-id="eb049-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="eb049-110">Les membres privés ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="eb049-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="eb049-111">Utilisation de DebuggerDisplayAttribute</span><span class="sxs-lookup"><span data-stu-id="eb049-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="eb049-112">Le constructeur <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> n’a qu’un seul argument : une chaîne à afficher dans la colonne valeur pour les instances du type.</span><span class="sxs-lookup"><span data-stu-id="eb049-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="eb049-113">Cette chaîne peut contenir des accolades ({ et }).</span><span class="sxs-lookup"><span data-stu-id="eb049-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="eb049-114">Le texte entre accolades est évalué comme une expression.</span><span class="sxs-lookup"><span data-stu-id="eb049-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="eb049-115">Par exemple, le code C# suivant entraîne l’affichage de « Count = 4 » quand le signe plus (+) est sélectionné pour développer l’affichage de débogueur pour une instance de `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="eb049-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="eb049-116">Les attributs appliqués aux propriétés référencées dans l’expression ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="eb049-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="eb049-117">Pour le compilateur C#, une expression générale est autorisée si elle n’a qu’un accès implicite à cette référence pour l’instance actuelle du type cible.</span><span class="sxs-lookup"><span data-stu-id="eb049-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="eb049-118">L’expression est limitée ; il n’existe aucun accès aux alias, aux variables locales ou aux pointeurs.</span><span class="sxs-lookup"><span data-stu-id="eb049-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="eb049-119">En code C#, vous pouvez utiliser une expression générale entre accolades qui dispose d’un accès implicite au pointeur `this` uniquement pour l’instance actuelle du type cible.</span><span class="sxs-lookup"><span data-stu-id="eb049-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="eb049-120">Par exemple, si un objet C# a un `ToString()` substitué, le débogueur appelle la substitution et affiche son résultat au lieu du `{<typeName>}.` standard. Ainsi, si vous avez substitué `ToString()`, vous n’avez pas besoin d’utiliser <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="eb049-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="eb049-121">Si vous utilisez les deux, l'attribut <xref:System.Diagnostics.DebuggerDisplayAttribute> prend la priorité sur la substitution de `ToString()`.</span><span class="sxs-lookup"><span data-stu-id="eb049-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="eb049-122">Utilisation de DebuggerBrowsableAttribute</span><span class="sxs-lookup"><span data-stu-id="eb049-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="eb049-123">Appliquez l’attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> à un champ ou une propriété pour spécifier comment il ou elle doit être affiché(e) dans la fenêtre du débogueur.</span><span class="sxs-lookup"><span data-stu-id="eb049-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="eb049-124">Le constructeur pour cet attribut prend l’une des valeurs d’énumération <xref:System.Diagnostics.DebuggerBrowsableState>, qui spécifie l’un des états suivants :</span><span class="sxs-lookup"><span data-stu-id="eb049-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="eb049-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indique que le membre n’est pas affiché dans la fenêtre de données.</span><span class="sxs-lookup"><span data-stu-id="eb049-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="eb049-126">Par exemple, l’utilisation de cette valeur pour <xref:System.Diagnostics.DebuggerBrowsableAttribute> sur un champ supprime le champ de la hiérarchie ; le champ n’est pas affiché quand vous développez le type englobant en cliquant sur le signe plus (+) pour l’instance de type.</span><span class="sxs-lookup"><span data-stu-id="eb049-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="eb049-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indique que le membre est affiché mais n’est pas développé par défaut.</span><span class="sxs-lookup"><span data-stu-id="eb049-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="eb049-128">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="eb049-128">This is the default behavior.</span></span>

- <span data-ttu-id="eb049-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indique que le membre proprement dit n’est pas affiché, mais ses objets constituants sont affichés s’il s’agit d’un tableau ou d’une collection.</span><span class="sxs-lookup"><span data-stu-id="eb049-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="eb049-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> n’est pas pris en charge par Visual Basic dans la version 2.0 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb049-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="eb049-131">L’exemple de code suivant illustre l’utilisation du <xref:System.Diagnostics.DebuggerBrowsableAttribute> pour empêcher la propriété qui le suit d’apparaître dans la fenêtre de débogage pour la classe.</span><span class="sxs-lookup"><span data-stu-id="eb049-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="eb049-132">Utilisation de DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="eb049-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="eb049-133">Utilisez l’attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> quand vous avez besoin de modifier radicalement l’affichage de débogage d’un type, sans toutefois changer le type proprement dit.</span><span class="sxs-lookup"><span data-stu-id="eb049-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="eb049-134">L’attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> sert à spécifier un proxy d’affichage pour un type, ce qui permet à un développeur de personnaliser l’affichage en fonction du type.</span><span class="sxs-lookup"><span data-stu-id="eb049-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="eb049-135">Cet attribut, à l’instar de <xref:System.Diagnostics.DebuggerDisplayAttribute>, peut être utilisé au niveau de l’assembly, auquel cas la propriété <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> spécifie le type pour lequel le proxy sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="eb049-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="eb049-136">Il est généralement recommandé que cet attribut spécifie un type imbriqué privé qui se produit dans le type auquel l’attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="eb049-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="eb049-137">Un évaluateur d’expression qui prend en charge les visionneuses de type vérifie la présence de cet attribut lors de l’affichage d’un type.</span><span class="sxs-lookup"><span data-stu-id="eb049-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="eb049-138">Si l’attribut est trouvé, l’évaluateur d’expression substitue le type du proxy d’affichage pour le type auquel l’attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="eb049-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="eb049-139">Quand <xref:System.Diagnostics.DebuggerTypeProxyAttribute> est présent, la fenêtre des variables du débogueur affiche uniquement les membres publics du type de proxy.</span><span class="sxs-lookup"><span data-stu-id="eb049-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="eb049-140">Les membres privés ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="eb049-140">Private members are not displayed.</span></span> <span data-ttu-id="eb049-141">Le comportement de la fenêtre de données n’est pas modifié par les affichages améliorés par les attributs.</span><span class="sxs-lookup"><span data-stu-id="eb049-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="eb049-142">Pour éviter une dégradation inutile des performances, les attributs du proxy d’affichage ne sont pas traités tant que l’objet n’est pas développé, soit par un clic de l’utilisateur sur le signe plus (+) en regard du type dans une fenêtre de données, soit par le biais de l’application de l’attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="eb049-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="eb049-143">Ainsi, nous vous recommandons de n’appliquer aucun attribut au type d’affichage.</span><span class="sxs-lookup"><span data-stu-id="eb049-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="eb049-144">Les attributs peuvent et doivent être appliqués dans le corps du type d’affichage.</span><span class="sxs-lookup"><span data-stu-id="eb049-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="eb049-145">L’exemple de code suivant montre comment utiliser <xref:System.Diagnostics.DebuggerTypeProxyAttribute> pour spécifier un type à utiliser en tant que proxy de l’affichage du débogueur.</span><span class="sxs-lookup"><span data-stu-id="eb049-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="eb049-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb049-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="eb049-147">Description</span><span class="sxs-lookup"><span data-stu-id="eb049-147">Description</span></span>

<span data-ttu-id="eb049-148">L’exemple de code suivant peut être affiché dans Visual Studio pour voir les résultats de l’application des attributs <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>et <xref:System.Diagnostics.DebuggerTypeProxyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="eb049-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="eb049-149">Code</span><span class="sxs-lookup"><span data-stu-id="eb049-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="eb049-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb049-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
