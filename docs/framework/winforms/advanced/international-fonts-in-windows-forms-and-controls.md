---
title: Polices internationales dans les formulaires et les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 59dde6bb384d644321a8ff5674d735f8e6d36fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743522"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="de5bc-102">Polices internationales dans les Windows Forms et les contrôles</span><span class="sxs-lookup"><span data-stu-id="de5bc-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="de5bc-103">Dans les applications internationales, la méthode recommandée pour sélectionner des polices consiste à utiliser la police de secours dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="de5bc-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="de5bc-104">La police de secours signifie que le système détermine à quel script appartient le caractère.</span><span class="sxs-lookup"><span data-stu-id="de5bc-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="de5bc-105">Utilisation de la police de secours</span><span class="sxs-lookup"><span data-stu-id="de5bc-105">Using font fallback</span></span>

<span data-ttu-id="de5bc-106">Pour tirer parti de cette fonctionnalité, ne définissez pas la propriété <xref:System.Drawing.Font> pour votre formulaire ou tout autre élément.</span><span class="sxs-lookup"><span data-stu-id="de5bc-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="de5bc-107">L’application utilisera automatiquement la police système par défaut, qui diffère d’une langue localisée du système d’exploitation à une autre.</span><span class="sxs-lookup"><span data-stu-id="de5bc-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="de5bc-108">Lorsque l’application s’exécute, le système fournit automatiquement la police correcte pour la culture sélectionnée dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="de5bc-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="de5bc-109">Il existe une exception à la règle qui consiste à ne pas définir la police, qui permet de modifier le style de police.</span><span class="sxs-lookup"><span data-stu-id="de5bc-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="de5bc-110">Cela peut être important pour une application dans laquelle l’utilisateur clique sur un bouton pour faire apparaître le texte dans une zone de texte en caractères gras.</span><span class="sxs-lookup"><span data-stu-id="de5bc-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="de5bc-111">Pour ce faire, vous devez écrire une fonction pour modifier le style de police de la zone de texte en gras, en fonction de la police du formulaire.</span><span class="sxs-lookup"><span data-stu-id="de5bc-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="de5bc-112">Il est important d’appeler cette fonction à deux emplacements : dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> du bouton et dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.FontChanged>.</span><span class="sxs-lookup"><span data-stu-id="de5bc-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="de5bc-113">Si la fonction est appelée uniquement dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> et qu’une autre partie du code modifie la famille de polices de la totalité du formulaire, la zone de texte ne change pas avec le reste du formulaire.</span><span class="sxs-lookup"><span data-stu-id="de5bc-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

<span data-ttu-id="de5bc-114">Toutefois, lorsque vous localisez votre application, la police en gras peut s’afficher mal pour certaines langues.</span><span class="sxs-lookup"><span data-stu-id="de5bc-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="de5bc-115">Si cela pose problème, vous souhaitez que les localisateurs aient la possibilité de basculer la police du gras en texte normal.</span><span class="sxs-lookup"><span data-stu-id="de5bc-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="de5bc-116">Étant donné que les localiseurs ne sont généralement pas des développeurs et n’ont pas accès au code source, seuls les fichiers de ressources, cette option doit être définie dans les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="de5bc-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="de5bc-117">Pour ce faire, vous devez affecter à la propriété <xref:System.Drawing.Font.Bold%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="de5bc-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="de5bc-118">Cela entraîne l’écriture du paramètre de police dans les fichiers de ressources, où les localiseurs peuvent le modifier.</span><span class="sxs-lookup"><span data-stu-id="de5bc-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="de5bc-119">Vous écrivez ensuite le code après la méthode `InitializeComponent` pour réinitialiser la police en fonction de la police du formulaire, mais en utilisant le style de police spécifié dans le fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="de5bc-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="de5bc-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de5bc-120">See also</span></span>

- [<span data-ttu-id="de5bc-121">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="de5bc-121">Using Fonts and Text</span></span>](using-fonts-and-text.md)
