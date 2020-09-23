---
title: Persistance d’un objet dans Visual Studio
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 0b2fff171164a29e6066839371fc95ad41b452f1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086463"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Procédure pas à pas : persistance d’un objet dans Visual Studio (Visual Basic)

Bien qu’il soit possible de définir des valeur par défaut pour les propriétés d’un objet au moment du design, les valeurs entrées lors de l’exécution sont perdues en cas de destruction de l’objet. Vous pouvez utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, ce qui vous permet de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.  
  
> [!NOTE]
> Dans Visual Basic, pour stocker des données simples, telles qu’un nom ou un nombre, vous pouvez utiliser l’objet `My.Settings`. Pour plus d’informations, consultez [My.Settings, objet](../../../language-reference/objects/my-settings-object.md).  
  
 Dans cette procédure pas à pas, vous allez créer un objet `Loan` simple et rendre ses données persistantes dans un fichier. Vous récupérerez ensuite les données du fichier lors de la recréation de l’objet.  
  
> [!IMPORTANT]
> Cet exemple crée un fichier s’il n’existe pas déjà. Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier. Les autorisations sont définies à l’aide de listes de contrôle d’accès. Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, ce qui représente une autorisation inférieure. Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier (plutôt que l’autorisation Créer sur un dossier). En outre, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.  
  
> [!IMPORTANT]
> Cet exemple stocke des données au format binaire. Ces formats ne doivent pas être utilisés pour des données sensibles, telles que les mots de passe ou les informations relatives à la carte de crédit.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Création de l’objet Loan  

 La première étape consiste à créer une classe `Loan` et une application de test qui utilise cette classe.  
  
### <a name="to-create-the-loan-class"></a>Pour créer la classe Loan  
  
1. Créez un projet Bibliothèque de classes et nommez-le « LoanClass ». Pour plus d’informations, consultez [Création de solutions et de projets](/visualstudio/ide/creating-solutions-and-projects).  
  
2. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le fichier Class1, puis choisissez **Renommer**. Renommez le fichier `Loan` et appuyez sur Entrée. Quand vous renommez le fichier, la classe est également renommée `Loan`.  
  
3. Ajoutez les membres publics suivants à la classe :  
  
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
  
 Vous devrez également créer une application simple qui utilise la classe `Loan`.  
  
### <a name="to-create-a-test-application"></a>Pour créer une application de test  
  
1. Pour ajouter un projet d’application Windows Forms à votre solution, dans le menu **Fichier**, choisissez **Ajouter**, **Nouveau projet**.  
  
2. Dans la boîte de dialogue **Ajouter un nouveau projet**, choisissez **Application Windows Forms** et entrez `LoanApp` comme nom du projet, puis cliquez sur **OK** pour fermer la boîte de dialogue.  
  
3. Dans l’**Explorateur de solutions**, choisissez le projet LoanApp.  
  
4. Dans le menu **Projet**, choisissez **Définir comme projet de démarrage**.  
  
5. Dans le menu **projet** , choisissez **Ajouter une référence**.  
  
6. Dans la boîte de dialogue **Ajouter une référence**, choisissez l’onglet **Projets**, puis le projet LoanClass.  
  
7. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
8. Dans le concepteur, ajoutez quatre contrôles <xref:System.Windows.Forms.TextBox> au formulaire.  
  
9. Dans l'éditeur de code, ajoutez le code suivant :  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. Ajoutez un gestionnaire d’événements pour l’événement `PropertyChanged` au formulaire en utilisant le code suivant :  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 À ce stade, vous pouvez générer et exécuter l’application. Notez que les valeurs par défaut de la classe `Loan` apparaissent dans les zones de texte. Essayez de remplacer le taux d’intérêt 7,5 par 7,1, puis fermez l’application et exécutez-la de nouveau : le taux reprend sa valeur par défaut de 7,5.  
  
 Dans la réalité, les taux d’intérêt changent régulièrement, mais pas nécessairement chaque fois que l’application est exécutée. Plutôt que d’imposer à l’utilisateur de mettre à jour le taux d’intérêt chaque fois qu’il exécute l’application, il peut être plus judicieux de conserver le taux d’intérêt le plus récent entre les instances de l’application. C’est ce que vous ferez à l’étape suivante, en ajoutant la sérialisation à la classe Loan.  
  
## <a name="using-serialization-to-persist-the-object"></a>Utilisation de la sérialisation pour rendre l’objet persistant  

 Pour rendre les valeurs de la classe Loan persistantes, vous devez d’abord marquer la classe avec l’attribut `Serializable`.  
  
### <a name="to-mark-a-class-as-serializable"></a>Pour marquer une classe comme étant sérialisable  
  
- Modifiez la déclaration de la classe Loan de la façon suivante :  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 L’attribut `Serializable` indique au compilateur que tout ce que contient la classe peut être persistant dans un fichier. Étant donné que l’événement `PropertyChanged` est géré par un objet Windows Form, il ne peut pas être sérialisé. L’attribut `NonSerialized` peut être utilisé pour marquer les membres de la classe qui ne doivent pas être persistants.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Pour empêcher la sérialisation d’un membre  
  
- Modifiez la déclaration de l’événement `PropertyChanged` comme suit :  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 L’étape suivante consiste à ajouter le code de sérialisation à l’application LoanApp. Pour sérialiser la classe et l’écrire dans un fichier, vous utiliserez les espaces de noms <xref:System.IO> et <xref:System.Xml.Serialization>. Pour éviter de taper les noms qualifiés complets, vous pouvez ajouter des références aux bibliothèques de classes requises.  
  
### <a name="to-add-references-to-namespaces"></a>Pour ajouter des références aux espaces de noms  
  
- Ajoutez les instructions suivantes au début de la classe `Form1` :  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     Dans ce cas, vous utilisez un formateur binaire pour enregistrer l’objet sous un format binaire.  
  
 L’étape suivante consiste à ajouter le code permettant de désérialiser l’objet à partir du fichier lors de la création de l’objet.  
  
### <a name="to-deserialize-an-object"></a>Pour désérialiser un objet  
  
1. Ajoutez une constante à la classe pour le nom de fichier des données sérialisées.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. Modifiez le code de la procédure événementielle `Form1_Load` de la façon suivante :  
  
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
  
     Notez que vous devez d’abord vérifier que le fichier existe. S’il existe, créez une classe <xref:System.IO.Stream> pour lire le fichier binaire et une classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour convertir le fichier. Vous devez également convertir le type de flux en type d’objet Loan.  
  
 Vous devez ensuite ajouter le code permettant d’enregistrer les données saisies dans les zones de texte dans la classe `Loan`, puis sérialiser la classe dans un fichier.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Pour enregistrer les données et sérialiser la classe  
  
- Ajoutez le code suivant à la procédure événementielle `Form1_FormClosing` :  
  
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
  
 À ce stade, vous pouvez de nouveau générer et exécuter l’application. À l’origine, les valeurs par défaut s’affichent dans les zones de texte. Essayez de modifier les valeurs et d’entrer un nom dans la quatrième zone de texte. Fermez l’application et exécutez-la de nouveau. Notez que les nouvelles valeurs s’affichent maintenant dans les zones de texte.  
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation (Visual Basic)](index.md)
- [Guide de programmation Visual Basic](../../index.md)
