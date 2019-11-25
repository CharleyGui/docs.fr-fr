---
title: Modèles de constructeur sécurisé pour DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 66e380a9428395c772d0dcfe45a995374774aec6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283830"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="017e2-102">Modèles de constructeur sécurisé pour DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="017e2-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="017e2-103">En règle générale, les constructeurs de classe ne doivent pas appeler des rappels tels que les méthodes ou les délégués virtuels, étant donné que les constructeurs peuvent être appelés comme une initialisation de base des constructeurs d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="017e2-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="017e2-104">L’utilisation de méthodes virtuelles peut se faire à un état d’initialisation incomplet d’un objet donné.</span><span class="sxs-lookup"><span data-stu-id="017e2-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="017e2-105">Toutefois, le système de propriétés appelle et expose les rappels en interne, dans le cadre du système de propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="017e2-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="017e2-106">Une opération aussi simple que la définition d’une valeur de propriété de dépendance avec <xref:System.Windows.DependencyObject.SetValue%2A> appel comprend potentiellement un rappel quelque part dans la détermination.</span><span class="sxs-lookup"><span data-stu-id="017e2-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="017e2-107">Pour cette raison, vous devez être prudent lorsque vous définissez des valeurs de propriété dans le corps d’un constructeur, car cela peut devenir problématique si votre type est utilisé comme classe de base de dépendance.</span><span class="sxs-lookup"><span data-stu-id="017e2-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="017e2-108">Il existe un modèle particulier pour l’implémentation des constructeurs <xref:System.Windows.DependencyObject> qui évite les problèmes spécifiques liés aux États des propriétés de dépendance et aux rappels inhérents, décrits ici.</span><span class="sxs-lookup"><span data-stu-id="017e2-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="017e2-109">Méthodes virtuelles de système de propriétés</span><span class="sxs-lookup"><span data-stu-id="017e2-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="017e2-110">Les méthodes virtuelles ou les rappels suivants sont potentiellement appelés pendant les calculs de l’appel de <xref:System.Windows.DependencyObject.SetValue%2A> qui définit une valeur de propriété de dépendance : <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="017e2-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="017e2-111">Chacune de ces méthodes virtuelles ou rappels sert une fonction spécifique pour étendre la souplesse du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et les dépendances de propriétés.</span><span class="sxs-lookup"><span data-stu-id="017e2-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="017e2-112">Pour plus d’informations sur l’utilisation de ces virtuels en vue de personnaliser la détermination des valeurs de propriété, consultez [Validation et rappels de propriétés de dépendance](dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="017e2-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="017e2-113">Application des règles FXCop et virtuelles du système de propriétés</span><span class="sxs-lookup"><span data-stu-id="017e2-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="017e2-114">Si vous utilisez l’outil Microsoft FXCop dans le cadre de votre processus de génération, et si vous dérivez de certaines classes de framework [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en appelant le constructeur de base, ou si vous implémentez vos propres propriétés de dépendance sur les classes dérivées, un message indiquant la violation d’une règle FXCop peut s’afficher.</span><span class="sxs-lookup"><span data-stu-id="017e2-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="017e2-115">La chaîne de nom de cette violation est la suivante :</span><span class="sxs-lookup"><span data-stu-id="017e2-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="017e2-116">Cette règle fait partie de la règle publique par défaut définie pour FXCop.</span><span class="sxs-lookup"><span data-stu-id="017e2-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="017e2-117">Elle peut signaler une trace, via le système de propriétés de dépendance, qui appelle une méthode virtuelle de système de propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="017e2-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="017e2-118">Le message indiquant une violation de règle peut continuer de s’afficher, même après l’application des modèles de constructeur recommandés documentés dans cette rubrique. Vous devrez donc peut-être désactiver ou supprimer cette règle dans la configuration de l’ensemble de règles FXCop.</span><span class="sxs-lookup"><span data-stu-id="017e2-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="017e2-119">La plupart des problèmes proviennent des classes dérivées, et non des classes existantes</span><span class="sxs-lookup"><span data-stu-id="017e2-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="017e2-120">Les problèmes signalés par cette règle se produisent lorsqu’une classe que vous implémentez avec des méthodes virtuelles dans sa séquence de construction est ensuite dérivée.</span><span class="sxs-lookup"><span data-stu-id="017e2-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="017e2-121">Si vous scellez la classe, ou si vous ne voulez pas qu’elle soit dérivée, les explications fournies ici et les problèmes liés aux règles FXCop ne s’appliquent pas.</span><span class="sxs-lookup"><span data-stu-id="017e2-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="017e2-122">Toutefois, si vous créez des classes qui sont destinées à être utilisées comme des classes de base, par exemple si vous créez des modèles ou un ensemble de bibliothèques de contrôles pouvant être développé, vous devez suivre les modèles recommandés ici pour les constructeurs.</span><span class="sxs-lookup"><span data-stu-id="017e2-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="017e2-123">Les constructeurs par défaut doivent initialiser toutes les valeurs demandées par les rappels</span><span class="sxs-lookup"><span data-stu-id="017e2-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="017e2-124">Tous les membres d’instance qui sont utilisés par vos substitutions de classe ou les rappels (les rappels de la liste dans la section des virtuels du système de propriétés) doivent être initialisés dans votre constructeur sans paramètre de classe, même si certaines de ces valeurs sont remplies par les valeurs « réelles » par le biais de paramètres des constructeurs sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="017e2-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class parameterless constructor, even if some of those values are filled by "real" values through parameters of the nonparameterless constructors.</span></span>  
  
 <span data-ttu-id="017e2-125">L’exemple ci-dessous, et ceux qui suivront, montrent du code C# qui enfreint cette règle et explique le problème :</span><span class="sxs-lookup"><span data-stu-id="017e2-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```csharp  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 <span data-ttu-id="017e2-126">Quand le code d’application appelle `new MyClass(objectvalue)`, cela appelle le constructeur sans paramètre et les constructeurs de classe de base.</span><span class="sxs-lookup"><span data-stu-id="017e2-126">When application code calls `new MyClass(objectvalue)`, this calls the parameterless constructor and base class constructors.</span></span> <span data-ttu-id="017e2-127">Il définit ensuite `Property1 = object1`, qui appelle la méthode virtuelle `OnPropertyChanged` sur le <xref:System.Windows.DependencyObject>propriétaire `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="017e2-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="017e2-128">La substitution référence `_myList`, qui n’a pas encore été initialisé.</span><span class="sxs-lookup"><span data-stu-id="017e2-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="017e2-129">Pour éviter ces problèmes, vérifiez que les rappels utilisent uniquement les autres propriétés de dépendance, et que cette propriété de dépendance a une valeur par défaut définie dans le cadre de ses métadonnées enregistrées.</span><span class="sxs-lookup"><span data-stu-id="017e2-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="017e2-130">Modèles de constructeur sécurisés</span><span class="sxs-lookup"><span data-stu-id="017e2-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="017e2-131">Pour éviter les risques d’initialisation incomplète si votre classe est utilisée comme classe de base, suivez ces modèles :</span><span class="sxs-lookup"><span data-stu-id="017e2-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a><span data-ttu-id="017e2-132">Constructeurs sans paramètre appelant l’initialisation de base</span><span class="sxs-lookup"><span data-stu-id="017e2-132">Parameterless constructors calling base initialization</span></span>  
 <span data-ttu-id="017e2-133">Implémentez ces constructeurs qui appellent la valeur de base par défaut :</span><span class="sxs-lookup"><span data-stu-id="017e2-133">Implement these constructors calling the base default:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="017e2-134">Constructeurs non définis par défaut (d’usage) ne correspondant à aucune signature de base</span><span class="sxs-lookup"><span data-stu-id="017e2-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="017e2-135">Si ces constructeurs utilisent les paramètres pour définir des propriétés de dépendance dans l’initialisation, commencez par appeler votre propre constructeur sans paramètre de classe pour l’initialisation, puis utilisez les paramètres pour définir les propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="017e2-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class parameterless constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="017e2-136">Il peut s’agir des propriétés de dépendance définies par votre classe ou des propriétés de dépendance héritées des classes de base. Dans les deux cas, utilisez le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="017e2-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="017e2-137">Constructeurs non définis par défaut (d’usage) correspondant à une signature de base</span><span class="sxs-lookup"><span data-stu-id="017e2-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="017e2-138">Au lieu d’appeler le constructeur de base avec le même paramétrage, appelez à nouveau votre propre classe « constructeur sans paramètre ».</span><span class="sxs-lookup"><span data-stu-id="017e2-138">Instead of calling the base constructor with the same parameterization, again call your own class' parameterless constructor.</span></span> <span data-ttu-id="017e2-139">N’appelez pas l’initialiseur de base, mais `this()`.</span><span class="sxs-lookup"><span data-stu-id="017e2-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="017e2-140">Reproduisez ensuite le comportement du constructeur d’origine en utilisant les paramètres passés comme des valeurs pour définir les propriétés nécessaires.</span><span class="sxs-lookup"><span data-stu-id="017e2-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="017e2-141">Utilisez la documentation du constructeur de base d’origine pour déterminer les propriétés que les paramètres sont censés définir :</span><span class="sxs-lookup"><span data-stu-id="017e2-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="017e2-142">Nécessité de correspondre à toutes les signatures</span><span class="sxs-lookup"><span data-stu-id="017e2-142">Must match all signatures</span></span>  
 <span data-ttu-id="017e2-143">Dans les cas où le type de base a plusieurs signatures, vous devez délibérément mettre en correspondance toutes les signatures possibles avec une implémentation de constructeur de votre propre classe qui utilise le modèle recommandé pour appeler le constructeur sans paramètre de classe avant de définir davantage sous.</span><span class="sxs-lookup"><span data-stu-id="017e2-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class parameterless constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="017e2-144">Définition de propriétés de dépendance avec SetValue</span><span class="sxs-lookup"><span data-stu-id="017e2-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="017e2-145">Ces mêmes modèles s’appliquent si vous définissez une propriété qui n’a pas de wrapper pour la commodité des paramètres de propriété et que vous définissez des valeurs avec <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="017e2-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="017e2-146">Vos appels à <xref:System.Windows.DependencyObject.SetValue%2A> qui passent par les paramètres du constructeur doivent également appeler le constructeur sans paramètre de la classe pour l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="017e2-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' parameterless constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017e2-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="017e2-147">See also</span></span>

- [<span data-ttu-id="017e2-148">Propriétés de dépendance personnalisées</span><span class="sxs-lookup"><span data-stu-id="017e2-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="017e2-149">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="017e2-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="017e2-150">Sécurité de propriété de dépendance</span><span class="sxs-lookup"><span data-stu-id="017e2-150">Dependency Property Security</span></span>](dependency-property-security.md)
