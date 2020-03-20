---
title: Propriétés de dépendance de type collection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: e783ce4b95b52b86671181dfe4b316d4b91d8fc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141535"
---
# <a name="collection-type-dependency-properties"></a>Propriétés de dépendance de type collection
Cette rubrique propose des conseils et des modèles suggérés pour l’implémentation d’une propriété de dépendance de type collection.  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a>Implémentation d’une propriété de dépendance de type collection  
 Pour une propriété de dépendance en général, le modèle de mise en œuvre que <xref:System.Windows.DependencyProperty> vous suivez est que vous définissez un emballage de propriété CLR, où cette propriété est soutenue par un identifiant plutôt qu’un champ ou une autre construction. Vous devez suivre ce même modèle quand vous implémentez une propriété de type collection. Cependant, une propriété de type collection introduit une certaine complexité au modèle chaque <xref:System.Windows.DependencyObject> <xref:System.Windows.Freezable> fois que le type qui est contenu dans la collection est lui-même une classe ou dérivée.  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a>Initialisation de la collection au-delà de la valeur par défaut  
 Quand vous créez une propriété de dépendance, vous ne spécifiez pas sa valeur par défaut comme étant la valeur de champ initiale. Vous la spécifiez à l’aide des métadonnées de la propriété de dépendance. Si votre propriété est un type référence, la valeur par défaut spécifiée dans les métadonnées de la propriété de dépendance n’est pas une valeur par défaut par instance, mais bien une valeur par défaut qui s’applique à toutes les instances du type. Ainsi, vous devez prendre garde de ne pas utiliser la collection statique unique définie par les métadonnées de la propriété de type collection comme valeur par défaut active pour les instances créées de votre type. À la place, vous devez vous assurer que vous affectez délibérément à la valeur de collection une collection (instance) unique dans le cadre de votre logique de constructeur de classe. Sinon, vous créerez une classe singleton involontaire.  
  
 Considérez l'exemple suivant. La section suivante de l’exemple `Aquarium`montre la définition d’une classe , qui contient un défaut avec la valeur par défaut. La classe définit la propriété `AquariumObjects`de dépendance <xref:System.Collections.Generic.List%601> de type <xref:System.Windows.FrameworkElement> de collecte, qui utilise le type générique avec une contrainte de type. Dans <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> l’appel pour la propriété de dépendance, les métadonnées établit la valeur par défaut pour être un nouveau générique <xref:System.Collections.Generic.List%601>.

> [!WARNING]
> Le code suivant ne se comporte pas correctement.

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Cependant, si vous laissez le code tel qu’illustré, cette valeur par défaut de liste unique est partagée pour toutes les instances d’`Aquarium`. Si vous avez exécuté le code de test suivant, qui a pour but de vous montrer comment instancier deux instances d’`Aquarium` distinctes et ajouter un `Fish` différent à chacune, vous risquez d’être surpris par le résultat :  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Au lieu d’avoir deux collections contenant chacune une unité, vous avez deux collections de deux unités ! En effet, chaque `Aquarium` a ajouté son `Fish` à la collection de valeurs par défaut, car il n’y a eu qu’un seul appel de constructeur dans les métadonnées, lequel a donc été partagé entre toutes les instances. Ce n’est sans doute pas ce que vous vouliez.  
  
 Pour résoudre ce problème, vous devez réinitialiser la valeur de la propriété de dépendance de type collection à une instance unique, dans le cadre de l’appel de constructeur de classe. Parce que la propriété est une propriété <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> de dépendance lisible <xref:System.Windows.DependencyPropertyKey> seulement, vous utilisez la méthode pour la définir, en utilisant le qui n’est accessible qu’au sein de la classe.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Si vous exécutez à nouveau ce même code de test, vous obtiendrez un résultat plus prévisible, où chaque `Aquarium` prend en charge sa propre collection unique.  
  
 Il peut y avoir une légère variation à ce modèle si vous choisissez d’avoir votre propriété de collection en lecture-écriture. Dans ce cas, vous pouvez appeler l’accesseur de l’ensemble public du constructeur pour <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> faire l’initialisation, qui <xref:System.Windows.DependencyProperty> serait toujours appeler la signature non clé de l’intérieur de votre emballage ensemble, à l’aide d’un identifiant public.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Signalement des modifications des valeurs de liaison des propriétés de collection  
 Une propriété de collection qui est elle-même une propriété de dépendance ne signale pas automatiquement les modifications apportées à ses sous-propriétés. Si vous créez des liaisons au sein d’une collection, cela peut empêcher la liaison de signaler les modifications et, de ce fait, invalider certains scénarios de liaison de données. Toutefois, si vous utilisez <xref:System.Windows.FreezableCollection%601> le type de collection comme type de collection, les modifications de sous-propriété aux éléments contenus de la collection sont correctement signalées, et les œuvres de liaison comme prévu.  
  
 Pour permettre une liaison de sous-propriété dans une collection <xref:System.Windows.FreezableCollection%601>d’objets de dépendance, créez <xref:System.Windows.DependencyObject> la propriété de collecte comme type, avec une contrainte de type pour cette collection à n’importe quelle classe dérivée.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FreezableCollection%601>
- [XAML et les classes personnalisées pour WPF](xaml-and-custom-classes-for-wpf.md)
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Aperçu des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
