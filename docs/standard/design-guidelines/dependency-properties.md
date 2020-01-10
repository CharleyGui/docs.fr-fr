---
title: Propriétés de dépendance
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: bd12d05dbba133503778e6df3cd0e6c3e5689d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709489"
---
# <a name="dependency-properties"></a>Propriétés de dépendance
Une propriété de dépendance (DP) est une propriété normale qui stocke sa valeur dans un magasin de propriétés au lieu de la stocker dans une variable de type (champ), par exemple.  
  
 Une propriété de dépendance attachée est un genre de propriété de dépendance modélisée en tant que méthodes d’extraction et de définition statiques représentant des « propriétés » qui décrivent les relations entre les objets et leurs conteneurs (par exemple, la position d’un objet `Button` sur un `Panel` conteneur).  
  
 **✓ DO** fournissent les propriétés de dépendance, si vous avez besoin des propriétés pour prendre en charge des fonctionnalités WPF telles que les styles, les déclencheurs, liaison de données, des animations, ressources dynamiques et d’héritage.  
  
## <a name="dependency-property-design"></a>Conception des propriétés de dépendance  
 **✓ DO** hériter <xref:System.Windows.DependencyObject>, ou l’un de ses sous-types, lors de l’implémentation des propriétés de dépendance. Le type fournit une implémentation très efficace d’une banque de propriétés et prend automatiquement en charge la liaison de données WPF.  
  
 **✓ DO** fournir une propriété CLR normale et un champ statique public en lecture seule le stockage d’une instance de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pour chaque propriété de dépendance.  
  
 **✓ DO** implémenter des propriétés de dépendance en appelant des méthodes d’instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> et <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** nom du champ de propriété de dépendance statique par suffixant le nom de la propriété « Property ».  
  
 **X DO NOT** définir explicitement les valeurs par défaut des propriétés de dépendance dans le code ; les définir dans les métadonnées.  
  
 Si vous définissez une propriété par défaut explicitement, vous pouvez empêcher la définition de cette propriété par certains moyens implicites, tels qu’un style.  
  
 **X DO NOT** placez le code dans les accesseurs de propriété autre que le code standard pour accéder au champ statique.  
  
 Ce code ne s’exécute pas si la propriété est définie par des moyens implicites, tels qu’un style, car le style utilise directement le champ statique.  
  
 **X DO NOT** utilise les propriétés de dépendance pour stocker des données sécurisées. Même les propriétés de dépendance privées sont accessibles publiquement.  
  
## <a name="attached-dependency-property-design"></a>Conception de propriété de dépendance attachée  
 Les propriétés de dépendance décrites dans la section précédente représentent des propriétés intrinsèques du type déclarant. par exemple, la propriété `Text` est une propriété de `TextButton`, qui la déclare. La propriété de dépendance attachée est un type spécial de propriété de dépendance.  
  
 La propriété <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> est un exemple classique d’une propriété jointe. La propriété représente la position de la colonne du bouton (et non de la grille), mais elle ne s’applique que si le bouton est contenu dans une grille et est donc « attaché » aux boutons par grilles.  
  
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
  
 La définition d’une propriété jointe ressemble principalement à celle d’une propriété de dépendance normale, sauf que les accesseurs sont représentés par des méthodes d’extraction et de définition statiques :  
  
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
  
## <a name="dependency-property-validation"></a>Validation de la propriété de dépendance  
 Les propriétés implémentent souvent ce que l’on appelle la validation. La logique de validation s’exécute lorsqu’une tentative est faite pour modifier la valeur d’une propriété.  
  
 Malheureusement, les accesseurs de propriété de dépendance ne peuvent pas contenir de code de validation arbitraire. Au lieu de cela, la logique de validation de la propriété de dépendance doit être spécifiée lors de l’inscription de la propriété.  
  
 **X DO NOT** placer la logique de validation de propriété de dépendance dans les accesseurs de la propriété. Au lieu de cela, passer un rappel de validation à `DependencyProperty.Register` méthode.  
  
## <a name="dependency-property-change-notifications"></a>Notifications de modification de propriété de dépendance  
 **X DO NOT** implémenter la logique de notification de modification dans les accesseurs de propriété de dépendance. Les propriétés de dépendance possèdent une fonctionnalité de notifications de modifications intégrée qui doit être utilisée en fournissant un rappel de notification de modification au <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Contrainte de valeur de propriété de dépendance  
 La contrainte de propriété a lieu lorsque la valeur donnée à un accesseur Set de propriété est modifiée par l’accesseur Set avant la modification réelle de la Banque de propriétés.  
  
 **X DO NOT** implémenter la logique de la contrainte dans les accesseurs de propriété de dépendance.  
  
 Les propriétés de dépendance ont une fonctionnalité de contrainte intégrée, et elles peuvent être utilisées en fournissant un rappel de contrainte au `PropertyMetadata`.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Modèles de design courants](../../../docs/standard/design-guidelines/common-design-patterns.md)
