---
title: Exécuter des procédures à intervalles définis à l’aide du composant Timer
description: Découvrez comment utiliser le composant Timer Windows Form pour exécuter des procédures à intervalles définis ou lorsqu’un intervalle de temps défini s’est écoulé.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: 6847819fcec98d01d38b8e44604a259f06be7c02
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325766"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="93cb5-103">Comment : exécuter des procédures à intervalles définis à l'aide du composant Timer Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93cb5-103">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="93cb5-104">Il peut arriver que vous souhaitiez créer une procédure qui s'exécute à intervalles réguliers jusqu'à ce qu'une boucle soit terminée ou qu'un intervalle de temps spécifique soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="93cb5-104">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="93cb5-105">Vous pouvez pour cela utiliser le composant <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="93cb5-105">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="93cb5-106">Ce composant est conçu pour un environnement Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="93cb5-106">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="93cb5-107">Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="93cb5-107">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93cb5-108">Il existe certaines limitations quand vous utilisez le composant <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="93cb5-108">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="93cb5-109">Pour plus d’informations, consultez [limitations de la propriété Interval du composant Timer Windows Forms](limitations-of-the-timer-component-interval-property.md).</span><span class="sxs-lookup"><span data-stu-id="93cb5-109">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](limitations-of-the-timer-component-interval-property.md).</span></span>  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="93cb5-110">Pour exécuter une procédure à intervalles spécifiques avec le composant Timer</span><span class="sxs-lookup"><span data-stu-id="93cb5-110">To run a procedure at set intervals with the Timer component</span></span>  
  
1. <span data-ttu-id="93cb5-111">Ajoutez un <xref:System.Windows.Forms.Timer> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="93cb5-111">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="93cb5-112">Pour savoir comment effectuer cette tâche par programmation, consultez la section suivante.</span><span class="sxs-lookup"><span data-stu-id="93cb5-112">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="93cb5-113">Visual Studio prend également en charge l’ajout de composants à un formulaire.</span><span class="sxs-lookup"><span data-stu-id="93cb5-113">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="93cb5-114">Consultez également [Comment : ajouter des contrôles sans interface utilisateur pour Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="93cb5-114">Also see [How to: Add Controls Without a User Interface to Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="93cb5-115">Définissez la propriété <xref:System.Windows.Forms.Timer.Interval%2A> (en millisecondes) du minuteur.</span><span class="sxs-lookup"><span data-stu-id="93cb5-115">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="93cb5-116">Cette propriété détermine combien de temps s'écoulera avant la réexécution de la procédure.</span><span class="sxs-lookup"><span data-stu-id="93cb5-116">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="93cb5-117">Plus un événement de minuteur se produit souvent, plus il faut de temps processeur pour y répondre.</span><span class="sxs-lookup"><span data-stu-id="93cb5-117">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="93cb5-118">Cela peut ralentir les performances globales.</span><span class="sxs-lookup"><span data-stu-id="93cb5-118">This can slow down overall performance.</span></span> <span data-ttu-id="93cb5-119">Ne définissez pas un intervalle plus petit que ce qui est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="93cb5-119">Do not set a smaller interval than you need.</span></span>  
  
3. <span data-ttu-id="93cb5-120">Écrivez le code approprié dans le gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick>.</span><span class="sxs-lookup"><span data-stu-id="93cb5-120">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="93cb5-121">Le code que vous écrivez dans cet événement s'exécutera à l'intervalle spécifié dans la propriété <xref:System.Windows.Forms.Timer.Interval%2A>.</span><span class="sxs-lookup"><span data-stu-id="93cb5-121">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4. <span data-ttu-id="93cb5-122">Affectez la valeur <xref:System.Windows.Forms.Timer.Enabled%2A> à la propriété `true` pour démarrer le minuteur.</span><span class="sxs-lookup"><span data-stu-id="93cb5-122">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="93cb5-123">L'événement <xref:System.Windows.Forms.Timer.Tick> commencera à se produire et à exécuter votre procédure à l'intervalle indiqué.</span><span class="sxs-lookup"><span data-stu-id="93cb5-123">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5. <span data-ttu-id="93cb5-124">Au moment opportun, affectez la valeur `false` à la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> pour empêcher que la procédure soit réexécutée.</span><span class="sxs-lookup"><span data-stu-id="93cb5-124">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="93cb5-125">La définition de l’intervalle sur `0` n’entraîne pas l’arrêt de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="93cb5-125">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93cb5-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="93cb5-126">Example</span></span>  
 <span data-ttu-id="93cb5-127">Ce premier exemple de code effectue le suivi de l'heure par incréments d'une seconde.</span><span class="sxs-lookup"><span data-stu-id="93cb5-127">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="93cb5-128">Il utilise un <xref:System.Windows.Forms.Button>, un <xref:System.Windows.Forms.Label> et un composant <xref:System.Windows.Forms.Timer> sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="93cb5-128">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="93cb5-129">La propriété <xref:System.Windows.Forms.Timer.Interval%2A> prend la valeur 1 000 (égal à une seconde).</span><span class="sxs-lookup"><span data-stu-id="93cb5-129">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="93cb5-130">Dans l'événement <xref:System.Windows.Forms.Timer.Tick>, la légende de l'étiquette prend comme valeur l'heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="93cb5-130">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="93cb5-131">En cas de clic sur le bouton, la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> prend la valeur `false` et le minuteur cesse de mettre à jour la légende de l'étiquette.</span><span class="sxs-lookup"><span data-stu-id="93cb5-131">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="93cb5-132">L’exemple de code suivant nécessite que vous disposiez d’un formulaire avec un <xref:System.Windows.Forms.Button> contrôle nommé `Button1` , d’un <xref:System.Windows.Forms.Timer> contrôle nommé `Timer1` et d’un <xref:System.Windows.Forms.Label> contrôle nommé `Label1` .</span><span class="sxs-lookup"><span data-stu-id="93cb5-132">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a><span data-ttu-id="93cb5-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="93cb5-133">Example</span></span>  
 <span data-ttu-id="93cb5-134">Ce deuxième exemple de code exécute une procédure toutes les 600 millisecondes jusqu'à ce qu'une boucle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="93cb5-134">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="93cb5-135">L’exemple de code suivant nécessite que vous disposiez d’un formulaire avec un <xref:System.Windows.Forms.Button> contrôle nommé `Button1` , d’un <xref:System.Windows.Forms.Timer> contrôle nommé `Timer1` et d’un <xref:System.Windows.Forms.Label> contrôle nommé `Label1` .</span><span class="sxs-lookup"><span data-stu-id="93cb5-135">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)
{  
   if (counter >= 10)
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="93cb5-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93cb5-136">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="93cb5-137">Timer, composant</span><span class="sxs-lookup"><span data-stu-id="93cb5-137">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="93cb5-138">Vue d'ensemble du composant Timer</span><span class="sxs-lookup"><span data-stu-id="93cb5-138">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
