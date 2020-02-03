---
title: Redimensionner le formulaire
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 8d4ce46ada505f952fc3090d10c5d893338d19f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739302"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="0768d-102">Comment : redimensionner des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0768d-102">How to: Resize Windows Forms</span></span>

<span data-ttu-id="0768d-103">Vous pouvez spécifier la taille de votre Windows Form de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="0768d-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="0768d-104">Vous pouvez modifier à la fois la hauteur et la largeur du formulaire par programmation en affectant une nouvelle valeur à la propriété <xref:System.Windows.Forms.Form.Size%2A>, ou ajuster les propriétés <xref:System.Windows.Forms.Control.Height%2A> et <xref:System.Windows.Forms.Control.Width%2A> individuellement.</span><span class="sxs-lookup"><span data-stu-id="0768d-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="0768d-105">Si vous utilisez Visual Studio, vous pouvez modifier la taille à l’aide de la Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0768d-105">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="0768d-106">Consultez également [Comment : redimensionner des Windows Forms à l’aide du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0768d-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="0768d-107">Redimensionner un formulaire par programmation</span><span class="sxs-lookup"><span data-stu-id="0768d-107">Resize a form programmatically</span></span>

<span data-ttu-id="0768d-108">Définissez la taille d'un formulaire au moment de l'exécution en définissant la propriété <xref:System.Windows.Forms.Form.Size%2A> du formulaire.</span><span class="sxs-lookup"><span data-stu-id="0768d-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="0768d-109">L'exemple de code suivant montre la taille de formulaire définie sur 100 × 100 pixels.</span><span class="sxs-lookup"><span data-stu-id="0768d-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="0768d-110">Modifier la largeur et la hauteur d’un formulaire par programmation</span><span class="sxs-lookup"><span data-stu-id="0768d-110">Change form width and height programmatically</span></span>

<span data-ttu-id="0768d-111">Une fois le <xref:System.Windows.Forms.Form.Size%2A> défini, modifiez la hauteur ou la largeur du formulaire à l'aide de la propriété <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="0768d-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="0768d-112">L'exemple de code suivant montre la largeur du formulaire définie sur 300 pixels à partir du bord gauche du formulaire, alors que la hauteur reste constante.</span><span class="sxs-lookup"><span data-stu-id="0768d-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="0768d-113">-ou-</span><span class="sxs-lookup"><span data-stu-id="0768d-113">-or-</span></span>

<span data-ttu-id="0768d-114">Modifiez <xref:System.Drawing.Size.Width%2A> ou <xref:System.Drawing.Size.Height%2A> en définissant la propriété <xref:System.Windows.Forms.Form.Size%2A>.</span><span class="sxs-lookup"><span data-stu-id="0768d-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="0768d-115">Toutefois, comme le montre l'exemple de code suivant, cette approche est plus laborieuse que la simple définition de la propriété <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="0768d-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="0768d-116">Modifier la taille de formulaire par incréments par programmation</span><span class="sxs-lookup"><span data-stu-id="0768d-116">Change form size by increments programmatically</span></span>

<span data-ttu-id="0768d-117">Pour incrémenter la taille du formulaire, définissez les propriétés <xref:System.Drawing.Size.Width%2A> et <xref:System.Drawing.Size.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="0768d-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="0768d-118">L'exemple de code suivant montre la largeur du formulaire définie sur 200 pixels de plus que la valeur actuelle.</span><span class="sxs-lookup"><span data-stu-id="0768d-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <span data-ttu-id="0768d-119">Utilisez toujours la propriété <xref:System.Drawing.Size.Height%2A> ou <xref:System.Drawing.Size.Width%2A> pour modifier une dimension d'un formulaire, sauf si vous définissez les dimensions de hauteur et de largeur en même temps en affectant une nouvelle structure <xref:System.Windows.Forms.Form.Size%2A> à la propriété <xref:System.Drawing.Size>.</span><span class="sxs-lookup"><span data-stu-id="0768d-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="0768d-120">La propriété <xref:System.Windows.Forms.Form.Size%2A> retourne une structure <xref:System.Drawing.Size>, qui est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="0768d-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="0768d-121">Vous ne pouvez pas attribuer une nouvelle valeur à la propriété d'un type valeur.</span><span class="sxs-lookup"><span data-stu-id="0768d-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="0768d-122">Le code suivant, par exemple, ne sera pas compilé :</span><span class="sxs-lookup"><span data-stu-id="0768d-122">Therefore, the following code example will not compile.</span></span>

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a><span data-ttu-id="0768d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0768d-123">See also</span></span>

- [<span data-ttu-id="0768d-124">Bien démarrer avec Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0768d-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="0768d-125">Amélioration des applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0768d-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
