---
title: Répondre aux modifications de jeu de polices dans une application Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739229"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="6bdce-102">Comment : répondre aux modifications de jeu de polices dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bdce-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="6bdce-103">Dans les systèmes d’exploitation Windows, un utilisateur peut modifier les paramètres de police à l’échelle du système pour que la police par défaut apparaisse plus grande ou plus petite.</span><span class="sxs-lookup"><span data-stu-id="6bdce-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="6bdce-104">La modification de ces paramètres de police est essentielle pour les utilisateurs qui sont affectés visuellement et qui nécessitent un plus grand type de lecture du texte sur leurs écrans.</span><span class="sxs-lookup"><span data-stu-id="6bdce-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="6bdce-105">Vous pouvez ajuster votre application Windows Forms pour réagir à ces modifications en accroissant ou en diminuant la taille du formulaire et de tout le texte contenu chaque fois que le jeu de polices change.</span><span class="sxs-lookup"><span data-stu-id="6bdce-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="6bdce-106">Si vous souhaitez que votre formulaire accepte les modifications de taille de police de manière dynamique, vous pouvez ajouter du code à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="6bdce-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="6bdce-107">En règle générale, la police par défaut utilisée par Windows Forms est la police retournée par l’appel de l’espace de noms <xref:Microsoft.Win32> à `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="6bdce-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="6bdce-108">La police retournée par cet appel change uniquement lorsque la résolution d’écran change.</span><span class="sxs-lookup"><span data-stu-id="6bdce-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="6bdce-109">Comme indiqué dans la procédure suivante, votre code doit modifier la police par défaut en <xref:System.Drawing.SystemFonts.IconTitleFont%2A> pour répondre aux modifications de la taille de police.</span><span class="sxs-lookup"><span data-stu-id="6bdce-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="6bdce-110">Pour utiliser la police du bureau et répondre aux modifications du jeu de polices</span><span class="sxs-lookup"><span data-stu-id="6bdce-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1. <span data-ttu-id="6bdce-111">Créez votre formulaire et ajoutez-y les contrôles qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="6bdce-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="6bdce-112">Pour plus d’informations, consultez [Comment : créer un Windows Forms application à partir de la ligne de commande](how-to-create-a-windows-forms-application-from-the-command-line.md) et des [contrôles à utiliser sur Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6bdce-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="6bdce-113">Ajoutez une référence à l’espace de noms <xref:Microsoft.Win32> dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6bdce-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="6bdce-114">Ajoutez le code suivant au constructeur de votre formulaire pour raccorder les gestionnaires d’événements requis et modifier la police par défaut en cours d’utilisation pour le formulaire.</span><span class="sxs-lookup"><span data-stu-id="6bdce-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="6bdce-115">Implémentez un gestionnaire pour l’événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> qui provoque la mise à l’échelle automatique du formulaire lorsque la catégorie <xref:Microsoft.Win32.UserPreferenceCategory.Window> change.</span><span class="sxs-lookup"><span data-stu-id="6bdce-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. <span data-ttu-id="6bdce-116">Enfin, implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.FormClosing> qui détache le gestionnaire d’événements <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="6bdce-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="6bdce-117">Si vous n’incluez pas ce code, votre application risque de provoquer une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="6bdce-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. <span data-ttu-id="6bdce-118">Compilez, puis exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="6bdce-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="6bdce-119">Pour modifier manuellement le jeu de polices dans Windows XP</span><span class="sxs-lookup"><span data-stu-id="6bdce-119">To manually change the font scheme in Windows XP</span></span>  
  
1. <span data-ttu-id="6bdce-120">Pendant que votre application Windows Forms est en cours d’exécution, cliquez avec le bouton droit sur le bureau Windows, puis choisissez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="6bdce-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="6bdce-121">Dans la boîte de dialogue **propriétés d’affichage** , cliquez sur l’onglet **apparence** .</span><span class="sxs-lookup"><span data-stu-id="6bdce-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3. <span data-ttu-id="6bdce-122">Dans la zone de liste déroulante taille de la **police** , sélectionnez une nouvelle taille de police.</span><span class="sxs-lookup"><span data-stu-id="6bdce-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="6bdce-123">Vous remarquerez que le formulaire réagit maintenant aux modifications au moment de l’exécution dans le schéma de police du bureau.</span><span class="sxs-lookup"><span data-stu-id="6bdce-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="6bdce-124">Lorsque l’utilisateur change de police **normale**, de **grandes polices**et de très **grandes polices**, le formulaire change la police et s’adapte correctement.</span><span class="sxs-lookup"><span data-stu-id="6bdce-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bdce-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="6bdce-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="6bdce-126">Le constructeur de cet exemple de code contient un appel à `InitializeComponent`, qui est défini lorsque vous créez un projet de Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bdce-126">The constructor in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="6bdce-127">Supprimez cette ligne de code si vous générez votre application sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="6bdce-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bdce-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bdce-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="6bdce-129">Mise à l'échelle automatique dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bdce-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
