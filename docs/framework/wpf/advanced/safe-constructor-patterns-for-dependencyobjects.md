---
title: Modèles de constructeur sécurisé pour DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 6d6ff444b99ca893e687731c56a48ea3ac072dd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187233"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Modèles de constructeur sécurisé pour DependencyObjects
En règle générale, les constructeurs de classe ne doivent pas appeler des rappels tels que les méthodes ou les délégués virtuels, étant donné que les constructeurs peuvent être appelés comme une initialisation de base des constructeurs d’une classe dérivée. L’utilisation de méthodes virtuelles peut se faire à un état d’initialisation incomplet d’un objet donné. Toutefois, le système de propriétés appelle et expose les rappels en interne, dans le cadre du système de propriétés de dépendance. Une opération aussi simple que l’établissement d’une valeur de propriété de dépendance avec <xref:System.Windows.DependencyObject.SetValue%2A> l’appel inclut potentiellement un rappel quelque part dans la détermination. Pour cette raison, vous devez être prudent lorsque vous définissez des valeurs de propriété dans le corps d’un constructeur, car cela peut devenir problématique si votre type est utilisé comme classe de base de dépendance. Il existe un modèle <xref:System.Windows.DependencyObject> particulier pour la mise en œuvre des constructeurs qui évite les problèmes spécifiques avec les états de propriété de dépendance et les rappels inhérents, qui est documenté ici.  

<a name="Property_System_Virtual_Methods"></a>
## <a name="property-system-virtual-methods"></a>Méthodes virtuelles de système de propriétés  
 Les méthodes virtuelles ou les rappels suivants sont potentiellement <xref:System.Windows.DependencyObject.SetValue%2A> appelés lors des calculs <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.PropertyChangedCallback>de <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>l’appel qui établit une valeur de propriété de dépendance: , , . Chacune de ces méthodes virtuelles ou rappels sert une fonction spécifique pour étendre la souplesse du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et les dépendances de propriétés. Pour plus d’informations sur l’utilisation de ces virtuels en vue de personnaliser la détermination des valeurs de propriété, consultez [Validation et rappels de propriétés de dépendance](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop Rule Enforcement vs Property System Virtuals  
 Si vous utilisez l’outil Microsoft FXCop dans le cadre de votre processus de génération, et si vous dérivez de certaines classes de framework [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en appelant le constructeur de base, ou si vous implémentez vos propres propriétés de dépendance sur les classes dérivées, un message indiquant la violation d’une règle FXCop peut s’afficher. La chaîne de nom de cette violation est la suivante :  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Cette règle fait partie de la règle publique par défaut définie pour FXCop. Elle peut signaler une trace, via le système de propriétés de dépendance, qui appelle une méthode virtuelle de système de propriété de dépendance. Le message indiquant une violation de règle peut continuer de s’afficher, même après l’application des modèles de constructeur recommandés documentés dans cette rubrique. Vous devrez donc peut-être désactiver ou supprimer cette règle dans la configuration de l’ensemble de règles FXCop.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>La plupart des problèmes proviennent des classes dérivées, et non des classes existantes  
 Les problèmes signalés par cette règle se produisent lorsqu’une classe que vous implémentez avec des méthodes virtuelles dans sa séquence de construction est ensuite dérivée. Si vous scellez la classe, ou si vous ne voulez pas qu’elle soit dérivée, les explications fournies ici et les problèmes liés aux règles FXCop ne s’appliquent pas. Toutefois, si vous créez des classes qui sont destinées à être utilisées comme des classes de base, par exemple si vous créez des modèles ou un ensemble de bibliothèques de contrôles pouvant être développé, vous devez suivre les modèles recommandés ici pour les constructeurs.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Les constructeurs par défaut doivent initialiser toutes les valeurs demandées par les rappels  
 Tout cas les membres qui sont utilisés par votre classe remplace ou rappelle (les rappels de la liste dans la section Virtuals du système de propriété) doivent être paralysés dans votre classe sans paramètres constructeur, même si certaines de ces valeurs sont remplies par des valeurs «réelles» par le biais paramètres des constructeurs non non-non-non-sans-parents.  
  
 L’exemple ci-dessous, et ceux qui suivront, montrent du code C# qui enfreint cette règle et explique le problème :  
  
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
  
 Lorsque le `new MyClass(objectvalue)`code d’application appelle, cela appelle le constructeur sans paramètres et les constructeurs de classe de base. Ensuite, `Property1 = object1`il définit , `OnPropertyChanged` qui appelle `MyClass` <xref:System.Windows.DependencyObject>la méthode virtuelle sur la possession .  La substitution référence `_myList`, qui n’a pas encore été initialisé.  
  
 Pour éviter ces problèmes, vérifiez que les rappels utilisent uniquement les autres propriétés de dépendance, et que cette propriété de dépendance a une valeur par défaut définie dans le cadre de ses métadonnées enregistrées.  
  
<a name="Safe_Constructor_Patterns"></a>
## <a name="safe-constructor-patterns"></a>Modèles de constructeur sécurisés  
 Pour éviter les risques d’initialisation incomplète si votre classe est utilisée comme classe de base, suivez ces modèles :  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Constructeurs sans paramètres appelant la initialisation de base  
 Implémentez ces constructeurs qui appellent la valeur de base par défaut :  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Constructeurs non définis par défaut (d’usage) ne correspondant à aucune signature de base  
 Si ces constructeurs utilisent les paramètres pour définir les propriétés de dépendance dans l’initialisation, appelez d’abord votre propre constructeur sans paramètres de classe pour l’initialisation, puis utilisez les paramètres pour définir les propriétés de dépendance. Il peut s’agir des propriétés de dépendance définies par votre classe ou des propriétés de dépendance héritées des classes de base. Dans les deux cas, utilisez le modèle suivant :  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Constructeurs non définis par défaut (d’usage) correspondant à une signature de base  
 Au lieu d’appeler le constructeur de base avec la même paramétrisation, encore une fois appeler le constructeur sans paramètres de votre propre classe. N’appelez pas l’initialiseur de base, mais `this()`. Reproduisez ensuite le comportement du constructeur d’origine en utilisant les paramètres passés comme des valeurs pour définir les propriétés nécessaires. Utilisez la documentation du constructeur de base d’origine pour déterminer les propriétés que les paramètres sont censés définir :  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Nécessité de correspondre à toutes les signatures  
 Pour les cas où le type de base a plusieurs signatures, vous devez délibérément faire correspondre toutes les signatures possibles avec une mise en œuvre constructeur de votre propre qui utilise le modèle recommandé d’appeler le constructeur sans paramètres de classe avant de définir plus loin Propriétés.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Définition de propriétés de dépendance avec SetValue  
 Ces mêmes modèles s’appliquent si vous établissez une propriété qui n’a pas un emballage pour la commodité de réglage de propriété, et définissent des valeurs avec <xref:System.Windows.DependencyObject.SetValue%2A>. Vos appels <xref:System.Windows.DependencyObject.SetValue%2A> à ce passage à travers les paramètres du constructeur doivent également appeler le constructeur sans paramètres de la classe pour l’initialisation.  
  
## <a name="see-also"></a>Voir aussi

- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Aperçu des propriétés de dépendance](dependency-properties-overview.md)
- [Sécurité de propriété de dépendance](dependency-property-security.md)
