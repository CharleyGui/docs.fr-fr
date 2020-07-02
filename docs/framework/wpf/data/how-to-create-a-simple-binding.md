---
title: 'Comment : créer une liaison simple'
description: Créez une liaison simple pour vos applications à l’aide de cet exemple de procédure dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618699"
---
# <a name="how-to-create-a-simple-binding"></a>Comment : créer une liaison simple
Cet exemple montre comment créer un simple <xref:System.Windows.Data.Binding> .  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName` . L' `Person` objet est défini dans l’espace de noms appelé `SDKSample` .  
  
 La ligne surlignée qui contient l' `<src>` élément dans l’exemple suivant instancie l' `Person` objet avec une `PersonName` valeur de propriété de `Joe` . Cette opération est effectuée dans la `Resources` section et assignée à un `x:Key` .  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 La ligne surlignée qui contient l' `<TextBlock>` élément lie ensuite le <xref:System.Windows.Controls.TextBlock> contrôle à la `PersonName` propriété. En conséquence, le <xref:System.Windows.Controls.TextBlock> s’affiche avec la valeur « Joe ».  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de procédures](data-binding-how-to-topics.md)
