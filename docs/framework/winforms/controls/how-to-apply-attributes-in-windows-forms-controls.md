---
title: 'Procédure : appliquer des attributs dans des contrôles Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 720172e9fcb13837b527d72176a35d366d83c948
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612824"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="84687-102">Procédure : appliquer des attributs dans des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84687-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="84687-103">Pour développer des composants et des contrôles qui interagissent correctement avec l’environnement de conception et s’exécutent correctement au moment de l’exécution, vous devez appliquer correctement des attributs aux classes et membres.</span><span class="sxs-lookup"><span data-stu-id="84687-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84687-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="84687-104">Example</span></span>  
 <span data-ttu-id="84687-105">L’exemple de code suivant montre comment utiliser plusieurs attributs sur un contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="84687-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="84687-106">Le contrôle montre une fonctionnalité de journalisation simple.</span><span class="sxs-lookup"><span data-stu-id="84687-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="84687-107">Lorsque le contrôle est lié à une source de données, il affiche les valeurs envoyées par la source de données dans un <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="84687-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="84687-108">Si une valeur dépasse la valeur spécifiée par le `Threshold` propriété, un `ThresholdExceeded` événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="84687-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="84687-109">Le `AttributesDemoControl` enregistre des valeurs avec une `LogEntry` classe.</span><span class="sxs-lookup"><span data-stu-id="84687-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="84687-110">Le `LogEntry` classe est une classe de modèle, ce qui signifie qu’elle est paramétrée sur le type qu’il journalise.</span><span class="sxs-lookup"><span data-stu-id="84687-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="84687-111">Par exemple, si le `AttributesDemoControl` enregistre des valeurs de type `float`, chaque `LogEntry` instance est déclarée et utilisée comme suit.</span><span class="sxs-lookup"><span data-stu-id="84687-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="84687-112">Étant donné que `LogEntry` est paramétré par un type arbitraire, il doit utiliser la réflexion pour fonctionner sur le type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="84687-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="84687-113">Pour la fonctionnalité de seuil fonctionne, le type de paramètre `T` doit implémenter le <xref:System.IComparable> interface.</span><span class="sxs-lookup"><span data-stu-id="84687-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="84687-114">Le formulaire qui héberge le `AttributesDemoControl` interroge périodiquement un compteur de performances.</span><span class="sxs-lookup"><span data-stu-id="84687-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="84687-115">Chaque valeur est empaquetée dans un `LogEntry` du type approprié et ajouté à la forme <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="84687-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="84687-116">Le `AttributesDemoControl` reçoit la valeur via sa liaison de données et affiche la valeur dans un <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="84687-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="84687-117">Le premier exemple de code est le `AttributesDemoControl` implémentation.</span><span class="sxs-lookup"><span data-stu-id="84687-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="84687-118">Le deuxième exemple de code montre un formulaire qui utilise le `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="84687-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="84687-119">Attributs de niveau classe</span><span class="sxs-lookup"><span data-stu-id="84687-119">Class-level Attributes</span></span>  
 <span data-ttu-id="84687-120">Certains attributs sont appliqués au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="84687-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="84687-121">L’exemple de code suivant montre les attributs qui sont couramment appliqués à un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="84687-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="84687-122">Attribut TypeConverter</span><span class="sxs-lookup"><span data-stu-id="84687-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="84687-123"><xref:System.ComponentModel.TypeConverterAttribute> est un autre attribut de niveau classe couramment utilisé.</span><span class="sxs-lookup"><span data-stu-id="84687-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="84687-124">L’exemple de code suivant illustre son utilisation pour la `LogEntry` classe.</span><span class="sxs-lookup"><span data-stu-id="84687-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="84687-125">Cet exemple illustre également une implémentation d’un <xref:System.ComponentModel.TypeConverter> pour le `LogEntry` type, appelé `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="84687-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="84687-126">Attributs au niveau de membre</span><span class="sxs-lookup"><span data-stu-id="84687-126">Member-level Attributes</span></span>  
 <span data-ttu-id="84687-127">Certains attributs sont appliqués au niveau du membre.</span><span class="sxs-lookup"><span data-stu-id="84687-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="84687-128">Les exemples de code suivants montrent certains attributs qui sont couramment appliqués aux propriétés des contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="84687-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="84687-129">Attribut de AmbientValue</span><span class="sxs-lookup"><span data-stu-id="84687-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="84687-130">L’exemple suivant montre le <xref:System.ComponentModel.AmbientValueAttribute> et affiche un code qui prend en charge son interaction avec l’environnement de conception.</span><span class="sxs-lookup"><span data-stu-id="84687-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="84687-131">Cette interaction est appelée *ambiance*.</span><span class="sxs-lookup"><span data-stu-id="84687-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="84687-132">Attributs de liaison de données</span><span class="sxs-lookup"><span data-stu-id="84687-132">Databinding Attributes</span></span>  
 <span data-ttu-id="84687-133">Les exemples suivants montrent une implémentation de la liaison de données complexe.</span><span class="sxs-lookup"><span data-stu-id="84687-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="84687-134">Niveau de la classe <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, comme indiqué précédemment, spécifie le `DataSource` et `DataMember` propriétés à utiliser pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="84687-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="84687-135">Le <xref:System.ComponentModel.AttributeProviderAttribute> Spécifie le type auquel le `DataSource` propriété liera.</span><span class="sxs-lookup"><span data-stu-id="84687-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84687-136">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="84687-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="84687-137">Le formulaire qui héberge le `AttributesDemoControl` requiert une référence à la `AttributesDemoControl` assembly afin de créer.</span><span class="sxs-lookup"><span data-stu-id="84687-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84687-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84687-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="84687-139">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84687-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="84687-140">Attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84687-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="84687-141">[Guide pratique pour Sérialiser des Collections de Types Standard avec DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="84687-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
