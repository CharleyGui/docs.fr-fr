---
title: 'Procédure : empêcher une tâche enfant de s’attacher à son parent'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
ms.openlocfilehash: 5ff181344e6437179fa77f11872ae9a47745be93
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288158"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Procédure : empêcher une tâche enfant de s’attacher à son parent
Ce document explique comment empêcher une tâche enfant de s’attacher à la tâche parente. Empêcher une tâche enfant de s’attacher à son parent est utile quand vous appelez un composant écrit par un tiers, qui utilise également des tâches. Par exemple, un composant tiers qui utilise l’option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> pour créer un objet <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> peut causer des problèmes dans votre code s’il est long ou s’il lève une exception non gérée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant compare les effets d’utiliser les options par défaut à ceux d’empêcher une tâche enfant de s’attacher au parent. L’exemple crée un objet <xref:System.Threading.Tasks.Task> qui appelle une bibliothèque tierce qui utilise également un objet <xref:System.Threading.Tasks.Task>. La bibliothèque tierce utilise l’option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> pour créer l’objet <xref:System.Threading.Tasks.Task>. L’application utilise l’option <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> pour créer la tâche parente. Cette option ordonne au runtime de supprimer la spécification <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> des tâches enfants.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Étant donné qu’une tâche parente ne se termine pas tant que toutes les tâches enfants ne sont pas achevées, une tâche enfant à exécution longue peut entraîner des performances médiocres de la part de l’application globale. Dans cet exemple, quand l’application utilise les options par défaut pour créer une tâche parente, la tâche enfant doit se terminer avant la fin de la tâche parente. Quand l’application utilise l’option <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, l’enfant n’est pas attachée au parent. Par conséquent, l’application peut effectuer du travail supplémentaire dès que la tâche parente est terminée et avant qu’elle ne doive attendre la fin de la tâche enfant.  
  
## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone basée sur les tâches](task-based-asynchronous-programming.md)
