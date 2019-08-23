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
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922786"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="a6779-102">Procédure : appliquer des attributs dans des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6779-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="a6779-103">Pour développer des composants et des contrôles qui interagissent correctement avec l’environnement de conception et s’exécutent correctement au moment de l’exécution, vous devez appliquer correctement les attributs aux classes et aux membres.</span><span class="sxs-lookup"><span data-stu-id="a6779-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6779-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a6779-104">Example</span></span>  
 <span data-ttu-id="a6779-105">L’exemple de code suivant montre comment utiliser plusieurs attributs sur un contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a6779-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="a6779-106">Le contrôle illustre une fonctionnalité de journalisation simple.</span><span class="sxs-lookup"><span data-stu-id="a6779-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="a6779-107">Lorsque le contrôle est lié à une source de données, il affiche les valeurs envoyées par la source de données <xref:System.Windows.Forms.DataGridView> dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="a6779-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a6779-108">Si une valeur dépasse la valeur spécifiée par la `Threshold` propriété, un `ThresholdExceeded` événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a6779-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="a6779-109">Les `AttributesDemoControl` valeurs des journaux avec `LogEntry` une classe.</span><span class="sxs-lookup"><span data-stu-id="a6779-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="a6779-110">La `LogEntry` classe est une classe de modèle, ce qui signifie qu’elle est paramétrée sur le type qu’elle enregistre.</span><span class="sxs-lookup"><span data-stu-id="a6779-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="a6779-111">Par exemple, si le `AttributesDemoControl` enregistre des valeurs de type `float`, chaque `LogEntry` instance est déclarée et utilisée comme suit.</span><span class="sxs-lookup"><span data-stu-id="a6779-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="a6779-112">Étant `LogEntry` donné que est paramétré par un type arbitraire, il doit utiliser la réflexion pour fonctionner sur le type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="a6779-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="a6779-113">Pour que la fonctionnalité de seuil fonctionne, le type `T` de paramètre doit <xref:System.IComparable> implémenter l’interface.</span><span class="sxs-lookup"><span data-stu-id="a6779-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="a6779-114">Formulaire qui héberge régulièrement les `AttributesDemoControl` requêtes d’un compteur de performance.</span><span class="sxs-lookup"><span data-stu-id="a6779-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="a6779-115">Chaque valeur est empaquetée `LogEntry` dans un du type approprié et ajoutée au du <xref:System.Windows.Forms.BindingSource>formulaire.</span><span class="sxs-lookup"><span data-stu-id="a6779-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="a6779-116">Le `AttributesDemoControl` reçoit la valeur par le biais de sa liaison de données et affiche <xref:System.Windows.Forms.DataGridView> la valeur dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="a6779-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="a6779-117">Le premier exemple de code est `AttributesDemoControl` l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="a6779-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="a6779-118">Le deuxième exemple de code illustre un formulaire qui utilise `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="a6779-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="a6779-119">Attributs au niveau de la classe</span><span class="sxs-lookup"><span data-stu-id="a6779-119">Class-level Attributes</span></span>  
 <span data-ttu-id="a6779-120">Certains attributs sont appliqués au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="a6779-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="a6779-121">L’exemple de code suivant affiche les attributs qui sont généralement appliqués à un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a6779-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="a6779-122">TypeConverter (attribut)</span><span class="sxs-lookup"><span data-stu-id="a6779-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="a6779-123"><xref:System.ComponentModel.TypeConverterAttribute>est un autre attribut couramment utilisé au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="a6779-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="a6779-124">L’exemple de code suivant illustre son utilisation pour `LogEntry` la classe.</span><span class="sxs-lookup"><span data-stu-id="a6779-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="a6779-125">Cet exemple montre également une implémentation de <xref:System.ComponentModel.TypeConverter> pour le `LogEntry` type, appelée `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="a6779-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="a6779-126">Attributs au niveau du membre</span><span class="sxs-lookup"><span data-stu-id="a6779-126">Member-level Attributes</span></span>  
 <span data-ttu-id="a6779-127">Certains attributs sont appliqués au niveau du membre.</span><span class="sxs-lookup"><span data-stu-id="a6779-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="a6779-128">Les exemples de code suivants montrent des attributs qui sont généralement appliqués aux propriétés des contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a6779-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="a6779-129">Attribut AmbientValue</span><span class="sxs-lookup"><span data-stu-id="a6779-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="a6779-130">L’exemple suivant illustre et <xref:System.ComponentModel.AmbientValueAttribute> montre le code qui prend en charge son interaction avec l’environnement de conception.</span><span class="sxs-lookup"><span data-stu-id="a6779-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="a6779-131">Cette interaction est appelée *ambiance*.</span><span class="sxs-lookup"><span data-stu-id="a6779-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="a6779-132">Attributs DataBinding</span><span class="sxs-lookup"><span data-stu-id="a6779-132">Databinding Attributes</span></span>  
 <span data-ttu-id="a6779-133">Les exemples suivants illustrent une implémentation d’une liaison de données complexe.</span><span class="sxs-lookup"><span data-stu-id="a6779-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="a6779-134">Le niveau <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>de classe, indiqué précédemment, spécifie les `DataMember` propriétés et à utiliser pour la `DataSource` liaison de données.</span><span class="sxs-lookup"><span data-stu-id="a6779-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="a6779-135">Spécifie le type auquel la `DataSource` propriété doit être liée. <xref:System.ComponentModel.AttributeProviderAttribute></span><span class="sxs-lookup"><span data-stu-id="a6779-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6779-136">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a6779-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="a6779-137">Le formulaire qui héberge le `AttributesDemoControl` requiert une référence à l' `AttributesDemoControl` assembly afin de générer.</span><span class="sxs-lookup"><span data-stu-id="a6779-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6779-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6779-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="a6779-139">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a6779-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="a6779-140">Attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6779-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="a6779-141">[Guide pratique : Sérialiser des collections de types standard avec DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a6779-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
