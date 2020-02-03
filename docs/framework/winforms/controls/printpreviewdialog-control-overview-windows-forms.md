---
title: Vue d'ensemble du contrôle PrintPreviewDialog
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 6fb971493336cda1e04c720dd09147e650918c3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741411"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="8fb8c-102">Vue d’ensemble du contrôle PrintPreviewDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8fb8c-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="8fb8c-103">Le contrôle Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> est une boîte de dialogue préconfigurée qui permet d’afficher la manière dont un [PrintDocument](printdocument-component-windows-forms.md) apparaîtra une fois imprimé.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="8fb8c-104">Utilisez-le au sein de votre application Windows comme une solution simple au lieu de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="8fb8c-105">Le contrôle contient des boutons pour l'impression, le zoom avant, l'affichage d'une ou plusieurs pages et la fermeture de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="8fb8c-106">Propriétés et méthodes de clé</span><span class="sxs-lookup"><span data-stu-id="8fb8c-106">Key properties and methods</span></span>

<span data-ttu-id="8fb8c-107">La propriété de clé du contrôle est <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, qui définit le document à afficher en aperçu.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="8fb8c-108">Le document doit être un objet <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="8fb8c-109">Pour afficher la boîte de dialogue, vous devez appeler sa méthode <xref:System.Windows.Forms.Form.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="8fb8c-110">L’anticrénelage peut rendre le texte plus lisse, mais peut également rendre l’affichage plus lent ; pour l’utiliser, affectez à la propriété <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="8fb8c-111">Certaines propriétés sont disponibles par le biais de la <xref:System.Windows.Forms.PrintPreviewControl> que la <xref:System.Windows.Forms.PrintPreviewDialog> contient.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="8fb8c-112">(Vous n’avez pas à ajouter ce <xref:System.Windows.Forms.PrintPreviewControl> au formulaire ; il est automatiquement contenu dans le <xref:System.Windows.Forms.PrintPreviewDialog> lorsque vous ajoutez la boîte de dialogue à votre formulaire.) Les propriétés <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, qui déterminent le nombre de pages affichées horizontalement et verticalement sur le contrôle, sont des exemples de propriétés disponibles par le biais du <xref:System.Windows.Forms.PrintPreviewControl>.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="8fb8c-113">Vous pouvez accéder à la propriété <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> en tant que `PrintPreviewDialog1.PrintPreviewControl.Columns` dans Visual Basic, C#`printPreviewDialog1.PrintPreviewControl.Columns` en Visual, ou C++`printPreviewDialog1->PrintPreviewControl->Columns` en Visual.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in Visual C++.</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="8fb8c-114">Performances de PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="8fb8c-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="8fb8c-115">Dans les conditions suivantes, le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> Initialise très lentement :</span><span class="sxs-lookup"><span data-stu-id="8fb8c-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="8fb8c-116">Une imprimante réseau est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-116">A network printer is used.</span></span>
- <span data-ttu-id="8fb8c-117">Les préférences de l’utilisateur pour cette imprimante, telles que les paramètres duplex, sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="8fb8c-118">Pour les applications qui s’exécutent sur le .NET Framework 4.5.2, vous pouvez ajouter la clé suivante à la section \<appSettings > de votre fichier de configuration pour améliorer les performances de l’initialisation de contrôle <xref:System.Windows.Forms.PrintPreviewDialog> :</span><span class="sxs-lookup"><span data-stu-id="8fb8c-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="8fb8c-119">Si la clé de `EnablePrintPreviewOptimization` est définie sur une autre valeur, ou si la clé n’est pas présente, l’optimisation n’est pas appliquée.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="8fb8c-120">Pour les applications qui s’exécutent sur le .NET Framework 4,6 ou versions ultérieures, vous pouvez ajouter le commutateur suivant à l’élément [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [\<Runtime >](../../configure-apps/file-schema/runtime/index.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="8fb8c-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="8fb8c-121">Si le commutateur n’est pas présent ou s’il est défini sur une autre valeur, l’optimisation n’est pas appliquée.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="8fb8c-122">Si vous utilisez l’événement <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> pour modifier les paramètres de l’imprimante, les performances du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> ne s’améliorent pas même si un commutateur de configuration d’optimisation est défini.</span><span class="sxs-lookup"><span data-stu-id="8fb8c-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fb8c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fb8c-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="8fb8c-124">Vue d’ensemble du contrôle PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="8fb8c-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="8fb8c-125">PrintPreviewDialog, contrôle</span><span class="sxs-lookup"><span data-stu-id="8fb8c-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="8fb8c-126">Contrôles et composants de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="8fb8c-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
