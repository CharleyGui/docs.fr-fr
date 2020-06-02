---
title: 'Procédure : définir et utiliser des fournisseurs de formats numériques personnalisés'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
ms.openlocfilehash: d12899fff7d9e6cb63728ba0b160b70fa2a41a1a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290511"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Procédure : définir et utiliser des fournisseurs de formats numériques personnalisés
Le .NET Framework vous donne un contrôle étendu sur la représentation sous forme de chaîne de valeurs numériques. Il prend en charge les fonctionnalités suivantes pour personnaliser le format des valeurs numériques :  
  
- Chaînes de format numériques standard, qui fournissent un ensemble prédéfini de formats pour convertir des nombres dans leur représentation sous forme de chaîne. Vous pouvez les utiliser avec toute méthode de mise en forme numérique, telle que <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, qui est dotée d’un paramètre `format`. Pour plus d’informations, consultez [Chaînes de format numériques standard](standard-numeric-format-strings.md).  
  
- Chaînes de format numériques personnalisées, qui fournissent un ensemble de symboles pouvant être combinés pour définir des spécificateurs de format numériques personnalisés. Elles peuvent également être utilisées avec toute méthode de mise en forme numérique, telle que <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, qui est dotée d’un paramètre `format`. Pour plus d’informations, consultez [Chaînes de format numériques personnalisées](custom-numeric-format-strings.md).  
  
- Personnalisez les objets <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo>, qui définissent les symboles et les modèles de format utilisés pour afficher les représentations sous forme de chaîne des valeurs numériques. Vous pouvez les utiliser avec toute méthode de mise en forme numérique, telle que <xref:System.Int32.ToString%2A>, qui est dotée d’un paramètre `provider`. En règle générale, le paramètre `provider` est utilisé pour spécifier une mise en forme propre à la culture.  
  
 Dans certains cas (par exemple, quand une application doit afficher un numéro de compte mis en forme, un numéro d’identification ou un code postal), ces trois techniques sont inappropriées. Le .NET Framework vous permet également de définir un objet de mise en forme qui n’est ni un objet <xref:System.Globalization.CultureInfo> ni un objet <xref:System.Globalization.NumberFormatInfo> pour déterminer la mise en forme d’une valeur numérique. Cette rubrique fournit des instructions détaillées pour l’implémentation de ce type d’objet et fournit un exemple qui met en forme les numéros de téléphone.  
  
### <a name="to-define-a-custom-format-provider"></a>Pour définir un fournisseur de format personnalisé  
  
1. Définir une classe qui implémente les inferfaces <xref:System.IFormatProvider> et <xref:System.ICustomFormatter>.  
  
2. Implémentez la méthode <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>. <xref:System.IFormatProvider.GetFormat%2A> est une méthode de rappel que la méthode de mise en forme (telle que la méthode <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>) appelle pour récupérer l’objet qui est réellement chargé d’effectuer la mise en forme personnalisée. Une implémentation type de <xref:System.IFormatProvider.GetFormat%2A> effectue les opérations suivantes :  
  
    1. Elle détermine si l’objet <xref:System.Type> passé comme paramètre de méthode représente une interface <xref:System.ICustomFormatter>.  
  
    2. Si le paramètre représente l’interface <xref:System.ICustomFormatter>, <xref:System.IFormatProvider.GetFormat%2A> retourne un objet qui implémente l’interface <xref:System.ICustomFormatter> chargée de fournir la mise en forme personnalisée. En général, l’objet de mise en forme personnalisée retourne lui-même.  
  
    3. Si le paramètre ne représente pas l’interface <xref:System.ICustomFormatter>, <xref:System.IFormatProvider.GetFormat%2A> retourne `null`.  
  
3. Implémentez la méthode <xref:System.ICustomFormatter.Format%2A>. Cette méthode est appelée par la méthode <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> et est chargée de retourner la représentation sous forme de chaîne d’un nombre. En général, l’implémentation de la méthode implique les étapes suivantes :  
  
    1. Le cas échéant, vérifiez que la méthode est légitimement destinée à fournir des services de mise en forme en examinant le paramètre `provider`. Pour les objets de mise en forme qui implémentent à la fois <xref:System.IFormatProvider> et <xref:System.ICustomFormatter>, vous devez déterminer si le paramètre `provider` correspond à l’objet de mise en forme actuel.  
  
    2. Déterminez si l’objet de mise en forme doit prendre en charge les spécificateurs de format personnalisés. (Par exemple, un spécificateur de format « N » peut indiquer qu’un numéro de téléphone américain doit être généré au format NANP, et un « I » peut indiquer une sortie au format E. 123 de la recommandation ITU-T.) Si les spécificateurs de format sont utilisés, la méthode doit gérer le spécificateur de format spécifique. Ill est passé à la méthode dans le paramètre `format`. Si aucun spécificateur n’est présent, la valeur du paramètre `format` est <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3. Récupérez la valeur numérique passée à la méthode comme paramètre `arg`. Effectuez toute opération requise pour le convertir en sa représentation sous forme de chaîne.  
  
    4. Retournez la représentation sous forme de chaîne du paramètre `arg`.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Pour utiliser un objet de mise en forme numérique personnalisé  
  
1. Créez une instance de la classe de mise en forme personnalisée.  
  
2. Appelez la méthode de mise en forme <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> en lui passant l’objet de mise en forme personnalisée, le spécificateur de mise en forme (ou <xref:System.String.Empty?displayProperty=nameWithType>, si aucun n’est utilisé) et la valeur numérique à mettre en forme.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un fournisseur de format numérique personnalisé nommé `TelephoneFormatter` qui convertit un nombre représentant un numéro de téléphone aux États-Unis au format NANP ou E.123 correspondant. La méthode gère deux spécificateurs de format, « N » (qui génère le format NANP) et « I » (qui génère le format E.123 international).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Le fournisseur de format numérique personnalisé peut être utilisé uniquement avec la méthode <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>. Les autres surcharges des méthodes de mise en forme numérique (telles que `ToString`) dotées d’un paramètre de type <xref:System.IFormatProvider> passent toutes à l’implémentation <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> un objet <xref:System.Type> qui représente le type <xref:System.Globalization.NumberFormatInfo>. La méthode doit normalement leur retourner un objet <xref:System.Globalization.NumberFormatInfo>. Si elle ne le fait pas, le fournisseur de format numérique personnalisé est ignoré et l’objet <xref:System.Globalization.NumberFormatInfo> pour la culture actuelle est utilisé à la place. Dans l’exemple, la méthode `TelephoneFormatter.GetFormat` vérifie si la transmission à une méthode de mise en forme numérique est effectuée de façon inappropriée ; elle examine le paramètre de méthode et retourne une valeur `null` si le type représenté n’est pas <xref:System.ICustomFormatter>.  
  
 Si un fournisseur de format numérique personnalisé prend en charge un jeu de spécificateurs de format, vérifiez que vous fournissez un comportement par défaut si aucun spécificateur de format n’est fourni dans l’élément de format utilisé dans l’appel de la méthode <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>. Dans l’exemple, « N » est le spécificateur de format par défaut. Cela permet de convertir un nombre en un numéro de téléphone mis en forme en fournissant un spécificateur de format explicite. L’exemple suivant illustre un appel de méthode de ce type.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Mais il permet également la conversion si aucun spécificateur de format n’est présent. L’exemple suivant illustre un appel de méthode de ce type.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Si aucun spécificateur de format par défaut n’est défini, votre implémentation de la méthode <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> doit inclure le code suivant afin que .NET puisse fournir la mise en forme que votre code ne prend pas en charge.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Dans le cas de cet exemple, la méthode qui implémente <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> est destinée à servir de méthode de rappel pour la méthode <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>. Ainsi, elle examine le paramètre `formatProvider` pour déterminer s’il contient une référence à l’objet `TelephoneFormatter` actuel. Toutefois, la méthode peut également être appelée directement à partir du code. Dans ce cas, vous pouvez utiliser le paramètre `formatProvider` pour fournir un objet <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> qui fournit des informations de mise en forme spécifiques à la culture.
