---
title: 'Comment : insérer des guillemets dans une chaîne'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: c14747291d6c41144eef97b258f852bbe14ef07d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735896"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="36ce3-102">Comment : insérer des guillemets dans une chaîne (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="36ce3-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="36ce3-103">Il se peut que vous souhaitiez placer une chaîne de texte entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="36ce3-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="36ce3-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="36ce3-104">For example:</span></span>  
  
 <span data-ttu-id="36ce3-105">Elle lui dit : « Cela vaut bien une récompense ! »</span><span class="sxs-lookup"><span data-stu-id="36ce3-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="36ce3-106">Vous pouvez également utiliser le champ <xref:Microsoft.VisualBasic.ControlChars.Quote> comme une constante.</span><span class="sxs-lookup"><span data-stu-id="36ce3-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="36ce3-107">Pour placer une chaîne entre guillemets dans votre code</span><span class="sxs-lookup"><span data-stu-id="36ce3-107">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="36ce3-108">Dans Visual Basic, insérez deux guillemets dans une ligne en tant que guillemet incorporé.</span><span class="sxs-lookup"><span data-stu-id="36ce3-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="36ce3-109">Dans Visual C# et Visual C++, insérez la séquence d’échappement \\«en tant que guillemet incorporé.</span><span class="sxs-lookup"><span data-stu-id="36ce3-109">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="36ce3-110">Par exemple, pour créer la chaîne précédente, utilisez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="36ce3-110">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="36ce3-111">-ou-</span><span class="sxs-lookup"><span data-stu-id="36ce3-111">-or-</span></span>  
  
2. <span data-ttu-id="36ce3-112">Insérez le caractère ASCII ou Unicode d’un guillemet.</span><span class="sxs-lookup"><span data-stu-id="36ce3-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="36ce3-113">Dans Visual Basic, utilisez le caractère ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="36ce3-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="36ce3-114">En Visual C#, utilisez le caractère Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="36ce3-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="36ce3-115">Dans cet exemple, vous ne pouvez pas utiliser \u0022, car vous ne pouvez pas utiliser un nom de caractère universel qui désigne un caractère dans le jeu de caractères de base.</span><span class="sxs-lookup"><span data-stu-id="36ce3-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="36ce3-116">Sinon, vous générez l’erreur C3851.</span><span class="sxs-lookup"><span data-stu-id="36ce3-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="36ce3-117">Pour plus d’informations, consultez [Erreur du compilateur C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="36ce3-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="36ce3-118">-ou-</span><span class="sxs-lookup"><span data-stu-id="36ce3-118">-or-</span></span>  
  
3. <span data-ttu-id="36ce3-119">Vous pouvez également définir une constante pour le caractère et l’utiliser lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="36ce3-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="36ce3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36ce3-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="36ce3-121">Vue d’ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="36ce3-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="36ce3-122">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36ce3-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="36ce3-123">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36ce3-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="36ce3-124">Guide pratique pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="36ce3-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="36ce3-125">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36ce3-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="36ce3-126">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36ce3-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="36ce3-127">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="36ce3-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
