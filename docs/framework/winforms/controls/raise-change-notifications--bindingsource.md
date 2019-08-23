---
title: 'Procédure : générer des notifications de modification à l’aide de BindingSource et de l’interface INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968289"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="6e682-102">Procédure : générer des notifications de modification à l’aide de BindingSource et de l’interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="6e682-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="6e682-103">Le composant <xref:System.Windows.Forms.BindingSource> détecte automatiquement les modifications apportées à une source de données quand le type contenu dans la source de données implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged> et déclenche des événements <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> quand une valeur de propriété est modifiée.</span><span class="sxs-lookup"><span data-stu-id="6e682-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="6e682-104">Cela est utile, car les contrôles liés à <xref:System.Windows.Forms.BindingSource> sont alors automatiquement mis à jour en cas de modification des valeurs de la source de données.</span><span class="sxs-lookup"><span data-stu-id="6e682-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e682-105">Si votre source de données implémente <xref:System.ComponentModel.INotifyPropertyChanged> et que vous exécutez des opérations asynchrones, vous ne devez pas modifier la source de données sur un thread d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="6e682-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="6e682-106">Au lieu de cela, vous devez lire les données sur un thread d’arrière-plan et les fusionner dans une liste sur le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6e682-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e682-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e682-107">Example</span></span>  
 <span data-ttu-id="6e682-108">L'exemple de code suivant illustre une implémentation simple de l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="6e682-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="6e682-109">Il montre également comment <xref:System.Windows.Forms.BindingSource> transmet automatiquement une modification de source de données à un contrôle lié quand <xref:System.Windows.Forms.BindingSource> est lié à une liste du type <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="6e682-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="6e682-110">Si vous utilisez l'attribut `CallerMemberName`, les appels à la méthode `NotifyPropertyChanged` ne doivent pas obligatoirement spécifier le nom de la propriété comme argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="6e682-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="6e682-111">Pour plus d’informations, consultez [informations surC#l’appelant ()](../../../csharp/programming-guide/concepts/caller-information.md) ou [informations sur l’appelant (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="6e682-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6e682-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6e682-112">Compiling the Code</span></span>  
 <span data-ttu-id="6e682-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="6e682-113">This example requires:</span></span>  
  
- <span data-ttu-id="6e682-114">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6e682-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e682-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e682-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="6e682-116">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="6e682-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="6e682-117">Guide pratique pour Déclencher des notifications de modifications à l’aide de la méthode ResetItem de BindingSource</span><span class="sxs-lookup"><span data-stu-id="6e682-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
