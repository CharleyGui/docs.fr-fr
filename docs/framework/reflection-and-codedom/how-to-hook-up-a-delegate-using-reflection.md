---
title: 'Procédure : raccorder un délégué à l’aide de la réflexion'
description: Consultez Guide pratique pour raccorder un délégué à l’aide de la réflexion dans .NET. Connectez une méthode existante à un événement en obtenant les types nécessaires via la réflexion.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: b5d93efd278a53a4e6382f2321918e58ead55899
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865084"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Procédure : raccorder un délégué à l’aide de la réflexion
Quand vous utilisez la réflexion pour charger et exécuter des assemblys, vous ne pouvez pas utiliser des fonctionnalités de langage telles que l’opérateur C#  ou l’instruction Visual BasicAddHandler pour raccorder des événements. Les procédures suivantes montrent comment raccorder une méthode existante à un événement en obtenant tous les types nécessaires par réflexion, et comment créer une méthode dynamique à l’aide de l’émission de réflexion et la raccorder à un événement.  
  
> [!NOTE]
> Pour découvrir une autre manière de raccorder un délégué de gestion des événements, consultez l’exemple de code relatif à la méthode <xref:System.Reflection.EventInfo.AddEventHandler%2A> de la classe <xref:System.Reflection.EventInfo>.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Pour raccorder un délégué à l’aide de la réflexion  
  
1. Chargez un assembly qui contient un type qui déclenche des événements. Les assemblys sont habituellement chargés avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>. Pour simplifier cet exemple, un formulaire dérivé dans l’assembly actuel est utilisé. La méthode <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> est donc utilisée pour charger l’assembly actuel.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Obtenez un objet <xref:System.Type> représentant le type et créez une instance du type. La méthode <xref:System.Activator.CreateInstance%28System.Type%29> est utilisée dans le code suivant car le formulaire a un constructeur sans paramètre. Vous pouvez utiliser plusieurs autres surcharges de la méthode <xref:System.Activator.CreateInstance%2A> si le type que vous créez n’a pas de constructeur sans paramètre. La nouvelle instance est stockée en tant que type <xref:System.Object> pour conserver l’illusion que l’assembly est inconnu. (La réflexion vous autorise à obtenir les types dans un assembly sans connaître leurs noms à l’avance.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Obtenez un objet <xref:System.Reflection.EventInfo> représentant l’événement, et utilisez la propriété <xref:System.Reflection.EventInfo.EventHandlerType%2A> pour obtenir le type de délégué utilisé pour gérer l’événement. Dans le code suivant, un <xref:System.Reflection.EventInfo> pour l’événement <xref:System.Windows.Forms.Control.Click> est obtenu.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Obtenez un objet <xref:System.Reflection.MethodInfo> représentant la méthode qui gère l’événement. Le code complet du programme dans la section Exemple plus loin dans cette rubrique contient une méthode qui correspond à la signature du délégué <xref:System.EventHandler>, qui gère l’événement <xref:System.Windows.Forms.Control.Click>, mais vous pouvez également générer des méthodes dynamiques au moment de l’exécution. Pour plus d’informations, consultez la procédure associée expliquant comment générer un gestionnaire d’événements au moment de l’exécution à l’aide d’une méthode dynamique.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Créez une instance du délégué à l’aide de la méthode <xref:System.Delegate.CreateDelegate%2A>. Cette méthode étant statique (`Shared` en Visual Basic), vous devez fournir le type délégué. Nous vous recommandons d’utiliser les surcharges de <xref:System.Delegate.CreateDelegate%2A> qui prennent un <xref:System.Reflection.MethodInfo>.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Obtenez la méthode d’accesseur `add` et appelez-la pour raccorder l’événement. Tous les événements ont un accesseur `add` et un accesseur `remove`, qui sont masqués par la syntaxe des langages de haut niveau. Par exemple, C# utilise l’opérateur `+=` pour raccorder des événements, et Visual Basic utilise l’[instruction AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md). Le code suivant obtient l’accesseur `add` de l’événement <xref:System.Windows.Forms.Control.Click> et l’appelle avec liaison tardive, en passant l’instance de délégué. Les arguments doivent être passés sous forme de tableau.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Testez l’événement. Le code suivant montre le formulaire défini dans l’exemple de code. Quand vous cliquez sur le formulaire, le gestionnaire d’événements est appelé.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Pour générer un gestionnaire d’événements au moment de l’exécution à l’aide d’une méthode dynamique  
  
1. Vous pouvez générer des méthodes de gestionnaire d’événements au moment de l’exécution, à l’aide de méthodes dynamiques légères et de l’émission de réflexion. Pour créer un gestionnaire d’événements, vous avez besoin du type de retour et des types de paramètres du délégué. Vous pouvez les obtenir en examinant la méthode `Invoke` du délégué. Le code suivant utilise les méthodes `GetDelegateReturnType` et `GetDelegateParameterTypes` pour obtenir ces informations. Vous trouverez le code de ces méthodes dans la section Exemple plus loin dans cette rubrique.  
  
     Comme il n’est pas nécessaire de nommer un <xref:System.Reflection.Emit.DynamicMethod>, la chaîne vide peut être utilisée. Dans le code suivant, le dernier argument associe la méthode dynamique au type actuel, ce qui donne au délégué accès à tous les membres privés et publics de la classe `Example`.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Générez un corps de méthode. Cette méthode charge une chaîne, appelle la surcharge de la méthode <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> qui prend une chaîne, dépile la valeur de retour (puisque le gestionnaire n’a aucun type de retour) et retourne. Pour en savoir plus sur l’émission de méthodes dynamiques, consultez [Guide pratique pour définir et exécuter des méthodes dynamiques](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Terminez l’exécution de la méthode dynamique en appelant sa méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>. Utilisez l’accesseur `add` pour ajouter le délégué à la liste d’appels de l’événement.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Testez l’événement. Le code suivant charge le formulaire défini dans l’exemple de code. Quand vous cliquez sur le formulaire, le gestionnaire d’événements prédéfini et le gestionnaire d’événements émis sont appelés.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment raccorder une méthode existante à un événement à l’aide de la réflexion, et également comment utiliser la classe <xref:System.Reflection.Emit.DynamicMethod> pour émettre une méthode au moment de l’exécution et la raccorder à un événement.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Procédure : définir et exécuter des méthodes dynamiques](how-to-define-and-execute-dynamic-methods.md)
- [Réflexion](reflection.md)
