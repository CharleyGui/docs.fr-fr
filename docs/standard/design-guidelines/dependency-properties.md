---
title: Propriétés de dépendance
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: e1372b75cb6501f8bc3fec913364e9d80157ad83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741722"
---
# <a name="dependency-properties"></a><span data-ttu-id="248d5-102">Propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="248d5-102">Dependency Properties</span></span>
<span data-ttu-id="248d5-103">Une propriété de dépendance (DP) est une propriété normale qui stocke sa valeur dans un magasin de propriétés au lieu de la stocker dans une variable de type (champ), par exemple.</span><span class="sxs-lookup"><span data-stu-id="248d5-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="248d5-104">Une propriété de dépendance attachée est un genre de propriété de dépendance modélisée en tant que méthodes d’extraction et de définition statiques représentant des « propriétés » qui décrivent les relations entre les objets et leurs conteneurs (par exemple, la position d’un objet `Button` sur un `Panel` conteneur).</span><span class="sxs-lookup"><span data-stu-id="248d5-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="248d5-105">✔️ fournissez les propriétés de dépendance, si vous avez besoin des propriétés pour prendre en charge des fonctionnalités WPF telles que le style, les déclencheurs, la liaison de données, les animations, les ressources dynamiques et l’héritage.</span><span class="sxs-lookup"><span data-stu-id="248d5-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="248d5-106">Conception des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="248d5-106">Dependency Property Design</span></span>
 <span data-ttu-id="248d5-107">✔️ héritent de <xref:System.Windows.DependencyObject>, ou de l’un de ses sous-types, lors de l’implémentation des propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="248d5-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="248d5-108">Le type fournit une implémentation très efficace d’une banque de propriétés et prend automatiquement en charge la liaison de données WPF.</span><span class="sxs-lookup"><span data-stu-id="248d5-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="248d5-109">✔️ fournissez une propriété CLR normale et un champ en lecture seule statique public qui stocke une instance de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pour chaque propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="248d5-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="248d5-110">✔️ Implémentez des propriétés de dépendance en appelant des méthodes d’instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> et <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="248d5-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="248d5-111">✔️ Nommez le champ statique de la propriété de dépendance en suffixant le nom de la propriété avec « Property ».</span><span class="sxs-lookup"><span data-stu-id="248d5-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="248d5-112">❌ ne définissez pas explicitement les valeurs par défaut des propriétés de dépendance dans le code ; Définissez-les plutôt dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="248d5-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="248d5-113">Si vous définissez une propriété par défaut explicitement, vous pouvez empêcher la définition de cette propriété par certains moyens implicites, tels qu’un style.</span><span class="sxs-lookup"><span data-stu-id="248d5-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="248d5-114">❌ ne placez pas de code dans les accesseurs de propriété autres que le code standard pour accéder au champ statique.</span><span class="sxs-lookup"><span data-stu-id="248d5-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="248d5-115">Ce code ne s’exécute pas si la propriété est définie par des moyens implicites, tels qu’un style, car le style utilise directement le champ statique.</span><span class="sxs-lookup"><span data-stu-id="248d5-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="248d5-116">❌ n’utilisez pas les propriétés de dépendance pour stocker des données sécurisées.</span><span class="sxs-lookup"><span data-stu-id="248d5-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="248d5-117">Même les propriétés de dépendance privées sont accessibles publiquement.</span><span class="sxs-lookup"><span data-stu-id="248d5-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="248d5-118">Conception de propriété de dépendance attachée</span><span class="sxs-lookup"><span data-stu-id="248d5-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="248d5-119">Les propriétés de dépendance décrites dans la section précédente représentent des propriétés intrinsèques du type déclarant. par exemple, la propriété `Text` est une propriété de `TextButton`, qui la déclare.</span><span class="sxs-lookup"><span data-stu-id="248d5-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="248d5-120">La propriété de dépendance attachée est un type spécial de propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="248d5-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="248d5-121">La propriété <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> est un exemple classique d’une propriété jointe.</span><span class="sxs-lookup"><span data-stu-id="248d5-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="248d5-122">La propriété représente la position de la colonne du bouton (et non de la grille), mais elle ne s’applique que si le bouton est contenu dans une grille et est donc « attaché » aux boutons par grilles.</span><span class="sxs-lookup"><span data-stu-id="248d5-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 <span data-ttu-id="248d5-123">La définition d’une propriété jointe ressemble principalement à celle d’une propriété de dépendance normale, sauf que les accesseurs sont représentés par des méthodes d’extraction et de définition statiques :</span><span class="sxs-lookup"><span data-stu-id="248d5-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a><span data-ttu-id="248d5-124">Validation de la propriété de dépendance</span><span class="sxs-lookup"><span data-stu-id="248d5-124">Dependency Property Validation</span></span>
 <span data-ttu-id="248d5-125">Les propriétés implémentent souvent ce que l’on appelle la validation.</span><span class="sxs-lookup"><span data-stu-id="248d5-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="248d5-126">La logique de validation s’exécute lorsqu’une tentative est faite pour modifier la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="248d5-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="248d5-127">Malheureusement, les accesseurs de propriété de dépendance ne peuvent pas contenir de code de validation arbitraire.</span><span class="sxs-lookup"><span data-stu-id="248d5-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="248d5-128">Au lieu de cela, la logique de validation de la propriété de dépendance doit être spécifiée lors de l’inscription de la propriété.</span><span class="sxs-lookup"><span data-stu-id="248d5-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="248d5-129">❌ ne placez pas la logique de validation de la propriété de dépendance dans les accesseurs de la propriété.</span><span class="sxs-lookup"><span data-stu-id="248d5-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="248d5-130">Au lieu de cela, passer un rappel de validation à `DependencyProperty.Register` méthode.</span><span class="sxs-lookup"><span data-stu-id="248d5-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="248d5-131">Notifications de modification de propriété de dépendance</span><span class="sxs-lookup"><span data-stu-id="248d5-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="248d5-132">❌ n’implémentez pas la logique de notification de modification dans les accesseurs de propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="248d5-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="248d5-133">Les propriétés de dépendance possèdent une fonctionnalité de notifications de modifications intégrée qui doit être utilisée en fournissant un rappel de notification de modification au <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="248d5-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="248d5-134">Contrainte de valeur de propriété de dépendance</span><span class="sxs-lookup"><span data-stu-id="248d5-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="248d5-135">La contrainte de propriété a lieu lorsque la valeur donnée à un accesseur Set de propriété est modifiée par l’accesseur Set avant la modification réelle de la Banque de propriétés.</span><span class="sxs-lookup"><span data-stu-id="248d5-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="248d5-136">❌ n’implémentez pas la logique de contrainte dans les accesseurs de propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="248d5-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="248d5-137">Les propriétés de dépendance ont une fonctionnalité de contrainte intégrée, et elles peuvent être utilisées en fournissant un rappel de contrainte au `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="248d5-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="248d5-138">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="248d5-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="248d5-139">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="248d5-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="248d5-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="248d5-140">See also</span></span>

- [<span data-ttu-id="248d5-141">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="248d5-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="248d5-142">Modèles de design courants</span><span class="sxs-lookup"><span data-stu-id="248d5-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)
