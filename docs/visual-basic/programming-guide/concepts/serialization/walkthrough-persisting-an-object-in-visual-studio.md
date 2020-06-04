---
title: Persistance d’un objet dans Visual Studio
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: e4eaf87c99ea1577d7f3ca40e628c00cc2700511
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413127"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="4a916-102">Procédure pas à pas : persistance d’un objet dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a916-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="4a916-103">Bien qu’il soit possible de définir des valeur par défaut pour les propriétés d’un objet au moment du design, les valeurs entrées lors de l’exécution sont perdues en cas de destruction de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4a916-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="4a916-104">Vous pouvez utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, ce qui vous permet de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4a916-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a916-105">Dans Visual Basic, pour stocker des données simples, telles qu’un nom ou un nombre, vous pouvez utiliser l’objet `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="4a916-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="4a916-106">Pour plus d’informations, consultez [My.Settings, objet](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="4a916-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="4a916-107">Dans cette procédure pas à pas, vous allez créer un objet `Loan` simple et rendre ses données persistantes dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="4a916-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="4a916-108">Vous récupérerez ensuite les données du fichier lors de la recréation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4a916-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4a916-109">Cet exemple crée un fichier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="4a916-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="4a916-110">Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier.</span><span class="sxs-lookup"><span data-stu-id="4a916-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="4a916-111">Les autorisations sont définies à l’aide de listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="4a916-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="4a916-112">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, ce qui représente une autorisation inférieure.</span><span class="sxs-lookup"><span data-stu-id="4a916-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="4a916-113">Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier (plutôt que l’autorisation Créer sur un dossier).</span><span class="sxs-lookup"><span data-stu-id="4a916-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="4a916-114">En outre, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.</span><span class="sxs-lookup"><span data-stu-id="4a916-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4a916-115">Cet exemple stocke des données au format binaire.</span><span class="sxs-lookup"><span data-stu-id="4a916-115">This example stores data in a binary.</span></span> <span data-ttu-id="4a916-116">Ces formats ne doivent pas être utilisés pour des données sensibles, telles que les mots de passe ou les informations relatives à la carte de crédit.</span><span class="sxs-lookup"><span data-stu-id="4a916-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a916-117">Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition.</span><span class="sxs-lookup"><span data-stu-id="4a916-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4a916-118">Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="4a916-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4a916-119">Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="4a916-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="4a916-120">Création de l’objet Loan</span><span class="sxs-lookup"><span data-stu-id="4a916-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="4a916-121">La première étape consiste à créer une classe `Loan` et une application de test qui utilise cette classe.</span><span class="sxs-lookup"><span data-stu-id="4a916-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="4a916-122">Pour créer la classe Loan</span><span class="sxs-lookup"><span data-stu-id="4a916-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="4a916-123">Créez un projet Bibliothèque de classes et nommez-le « LoanClass ».</span><span class="sxs-lookup"><span data-stu-id="4a916-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="4a916-124">Pour plus d’informations, consultez [Création de solutions et de projets](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="4a916-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="4a916-125">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le fichier Class1, puis choisissez **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="4a916-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="4a916-126">Renommez le fichier `Loan` et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="4a916-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="4a916-127">Quand vous renommez le fichier, la classe est également renommée `Loan`.</span><span class="sxs-lookup"><span data-stu-id="4a916-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="4a916-128">Ajoutez les membres publics suivants à la classe :</span><span class="sxs-lookup"><span data-stu-id="4a916-128">Add the following public members to the class:</span></span>  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 <span data-ttu-id="4a916-129">Vous devrez également créer une application simple qui utilise la classe `Loan`.</span><span class="sxs-lookup"><span data-stu-id="4a916-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="4a916-130">Pour créer une application de test</span><span class="sxs-lookup"><span data-stu-id="4a916-130">To create a test application</span></span>  
  
1. <span data-ttu-id="4a916-131">Pour ajouter un projet d’application Windows Forms à votre solution, dans le menu **Fichier**, choisissez **Ajouter**, **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="4a916-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="4a916-132">Dans la boîte de dialogue **Ajouter un nouveau projet**, choisissez **Application Windows Forms** et entrez `LoanApp` comme nom du projet, puis cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4a916-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="4a916-133">Dans l’**Explorateur de solutions**, choisissez le projet LoanApp.</span><span class="sxs-lookup"><span data-stu-id="4a916-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="4a916-134">Dans le menu **Projet**, choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="4a916-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="4a916-135">Dans le menu **projet** , choisissez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="4a916-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="4a916-136">Dans la boîte de dialogue **Ajouter une référence**, choisissez l’onglet **Projets**, puis le projet LoanClass.</span><span class="sxs-lookup"><span data-stu-id="4a916-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="4a916-137">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4a916-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="4a916-138">Dans le concepteur, ajoutez quatre contrôles <xref:System.Windows.Forms.TextBox> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="4a916-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="4a916-139">Dans l'éditeur de code, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4a916-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="4a916-140">Ajoutez un gestionnaire d’événements pour l’événement `PropertyChanged` au formulaire en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4a916-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="4a916-141">À ce stade, vous pouvez générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="4a916-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="4a916-142">Notez que les valeurs par défaut de la classe `Loan` apparaissent dans les zones de texte.</span><span class="sxs-lookup"><span data-stu-id="4a916-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="4a916-143">Essayez de remplacer le taux d’intérêt 7,5 par 7,1, puis fermez l’application et exécutez-la de nouveau : le taux reprend sa valeur par défaut de 7,5.</span><span class="sxs-lookup"><span data-stu-id="4a916-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="4a916-144">Dans la réalité, les taux d’intérêt changent régulièrement, mais pas nécessairement chaque fois que l’application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="4a916-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="4a916-145">Plutôt que d’imposer à l’utilisateur de mettre à jour le taux d’intérêt chaque fois qu’il exécute l’application, il peut être plus judicieux de conserver le taux d’intérêt le plus récent entre les instances de l’application.</span><span class="sxs-lookup"><span data-stu-id="4a916-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="4a916-146">C’est ce que vous ferez à l’étape suivante, en ajoutant la sérialisation à la classe Loan.</span><span class="sxs-lookup"><span data-stu-id="4a916-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="4a916-147">Utilisation de la sérialisation pour rendre l’objet persistant</span><span class="sxs-lookup"><span data-stu-id="4a916-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="4a916-148">Pour rendre les valeurs de la classe Loan persistantes, vous devez d’abord marquer la classe avec l’attribut `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="4a916-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="4a916-149">Pour marquer une classe comme étant sérialisable</span><span class="sxs-lookup"><span data-stu-id="4a916-149">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="4a916-150">Modifiez la déclaration de la classe Loan de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="4a916-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="4a916-151">L’attribut `Serializable` indique au compilateur que tout ce que contient la classe peut être persistant dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="4a916-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="4a916-152">Étant donné que l’événement `PropertyChanged` est géré par un objet Windows Form, il ne peut pas être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="4a916-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="4a916-153">L’attribut `NonSerialized` peut être utilisé pour marquer les membres de la classe qui ne doivent pas être persistants.</span><span class="sxs-lookup"><span data-stu-id="4a916-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="4a916-154">Pour empêcher la sérialisation d’un membre</span><span class="sxs-lookup"><span data-stu-id="4a916-154">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="4a916-155">Modifiez la déclaration de l’événement `PropertyChanged` comme suit :</span><span class="sxs-lookup"><span data-stu-id="4a916-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="4a916-156">L’étape suivante consiste à ajouter le code de sérialisation à l’application LoanApp.</span><span class="sxs-lookup"><span data-stu-id="4a916-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="4a916-157">Pour sérialiser la classe et l’écrire dans un fichier, vous utiliserez les espaces de noms <xref:System.IO> et <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="4a916-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="4a916-158">Pour éviter de taper les noms qualifiés complets, vous pouvez ajouter des références aux bibliothèques de classes requises.</span><span class="sxs-lookup"><span data-stu-id="4a916-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="4a916-159">Pour ajouter des références aux espaces de noms</span><span class="sxs-lookup"><span data-stu-id="4a916-159">To add references to namespaces</span></span>  
  
- <span data-ttu-id="4a916-160">Ajoutez les instructions suivantes au début de la classe `Form1` :</span><span class="sxs-lookup"><span data-stu-id="4a916-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="4a916-161">Dans ce cas, vous utilisez un formateur binaire pour enregistrer l’objet sous un format binaire.</span><span class="sxs-lookup"><span data-stu-id="4a916-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="4a916-162">L’étape suivante consiste à ajouter le code permettant de désérialiser l’objet à partir du fichier lors de la création de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4a916-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="4a916-163">Pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="4a916-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="4a916-164">Ajoutez une constante à la classe pour le nom de fichier des données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="4a916-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="4a916-165">Modifiez le code de la procédure événementielle `Form1_Load` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="4a916-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     <span data-ttu-id="4a916-166">Notez que vous devez d’abord vérifier que le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="4a916-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="4a916-167">S’il existe, créez une classe <xref:System.IO.Stream> pour lire le fichier binaire et une classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour convertir le fichier.</span><span class="sxs-lookup"><span data-stu-id="4a916-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="4a916-168">Vous devez également convertir le type de flux en type d’objet Loan.</span><span class="sxs-lookup"><span data-stu-id="4a916-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="4a916-169">Vous devez ensuite ajouter le code permettant d’enregistrer les données saisies dans les zones de texte dans la classe `Loan`, puis sérialiser la classe dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="4a916-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="4a916-170">Pour enregistrer les données et sérialiser la classe</span><span class="sxs-lookup"><span data-stu-id="4a916-170">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="4a916-171">Ajoutez le code suivant à la procédure événementielle `Form1_FormClosing` :</span><span class="sxs-lookup"><span data-stu-id="4a916-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 <span data-ttu-id="4a916-172">À ce stade, vous pouvez de nouveau générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="4a916-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="4a916-173">À l’origine, les valeurs par défaut s’affichent dans les zones de texte.</span><span class="sxs-lookup"><span data-stu-id="4a916-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="4a916-174">Essayez de modifier les valeurs et d’entrer un nom dans la quatrième zone de texte.</span><span class="sxs-lookup"><span data-stu-id="4a916-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="4a916-175">Fermez l’application et exécutez-la de nouveau.</span><span class="sxs-lookup"><span data-stu-id="4a916-175">Close the application and then run it again.</span></span> <span data-ttu-id="4a916-176">Notez que les nouvelles valeurs s’affichent maintenant dans les zones de texte.</span><span class="sxs-lookup"><span data-stu-id="4a916-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a916-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a916-177">See also</span></span>

- [<span data-ttu-id="4a916-178">Sérialisation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a916-178">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="4a916-179">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a916-179">Visual Basic Programming Guide</span></span>](../../index.md)
