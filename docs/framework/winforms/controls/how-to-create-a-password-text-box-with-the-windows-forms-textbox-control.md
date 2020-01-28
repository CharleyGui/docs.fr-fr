---
title: Créer une zone de texte de mot de passe avec le contrôle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: ff4706a736d15f14cf437c808219e9088773dc6d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731283"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="b2bf9-102">Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2bf9-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>

<span data-ttu-id="b2bf9-103">Une zone de mot de passe est une zone de texte Windows Forms qui affiche des espaces réservés lorsqu’un utilisateur tape une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>

### <a name="to-create-a-password-text-box"></a><span data-ttu-id="b2bf9-104">Pour créer une zone de texte de mot de passe</span><span class="sxs-lookup"><span data-stu-id="b2bf9-104">To create a password text box</span></span>

1. <span data-ttu-id="b2bf9-105">Affectez à la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> du contrôle <xref:System.Windows.Forms.TextBox> la valeur d’un caractère spécifique.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>

    <span data-ttu-id="b2bf9-106">La propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> spécifie le caractère affiché dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="b2bf9-107">Par exemple, si vous souhaitez que les astérisques s’affichent dans la zone mot de passe, spécifiez \* pour la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> dans le Fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="b2bf9-108">Ensuite, quel que soit le caractère qu’un utilisateur tape dans la zone de texte, un astérisque s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>

2. <span data-ttu-id="b2bf9-109">Facultatif Définissez la propriété <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="b2bf9-110">La propriété détermine le nombre de caractères pouvant être tapés dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="b2bf9-111">Si la longueur maximale est dépassée, le système émet un signal sonore et la zone de texte n’accepte plus de caractères.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="b2bf9-112">Notez que vous n’avez peut-être pas besoin d’effectuer cette opération, car la longueur maximale d’un mot de passe peut être utilisée par les pirates qui essaient de deviner le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>

    <span data-ttu-id="b2bf9-113">L’exemple de code suivant montre comment initialiser une zone de texte qui accepte une chaîne d’une longueur maximale de 14 caractères et afficher des astérisques à la place de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="b2bf9-114">La procédure `InitializeMyControl` ne s’exécute pas automatiquement ; elle doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b2bf9-115">L’utilisation de la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> sur une zone de texte permet de s’assurer que les autres utilisateurs ne seront pas en mesure de déterminer le mot de passe d’un utilisateur s’ils observent la saisie de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="b2bf9-116">Cette mesure de sécurité ne couvre pas le type de stockage ou la transmission du mot de passe qui peut se produire en raison de la logique de votre application.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="b2bf9-117">Étant donné que le texte entré n’est pas chiffré, vous devez le traiter comme n’importe quelle autre donnée confidentielle.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="b2bf9-118">Même s’il n’apparaît pas comme tel, le mot de passe est toujours traité comme une chaîne de texte brut (sauf si vous avez implémenté une mesure de sécurité supplémentaire).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>

    ```vb
    Private Sub InitializeMyControl()
       ' Set to no text.
       TextBox1.Text = ""
       ' The password character is an asterisk.
       TextBox1.PasswordChar = "*"
       ' The control will allow no more than 14 characters.
       TextBox1.MaxLength = 14
    End Sub
    ```

    ```csharp
    private void InitializeMyControl()
    {
       // Set to no text.
       textBox1.Text = "";
       // The password character is an asterisk.
       textBox1.PasswordChar = '*';
       // The control will allow no more than 14 characters.
       textBox1.MaxLength = 14;
    }
    ```

    ```cpp
    private:
       void InitializeMyControl()
       {
          // Set to no text.
          textBox1->Text = "";
          // The password character is an asterisk.
          textBox1->PasswordChar = '*';
          // The control will allow no more than 14 characters.
          textBox1->MaxLength = 14;
       }
    ```

## <a name="see-also"></a><span data-ttu-id="b2bf9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2bf9-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="b2bf9-120">Vue d’ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="b2bf9-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="b2bf9-121">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2bf9-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="b2bf9-122">Guide pratique pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="b2bf9-122">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="b2bf9-123">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="b2bf9-123">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="b2bf9-124">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2bf9-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b2bf9-125">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2bf9-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b2bf9-126">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="b2bf9-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
