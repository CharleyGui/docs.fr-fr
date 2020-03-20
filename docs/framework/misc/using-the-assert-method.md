---
title: Utilisation de la méthode Assert
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181101"
---
# <a name="using-the-assert-method"></a>Utilisation de la méthode Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> est une méthode qui peut être appelée sur les classes d'autorisation d'accès au code et sur la classe <xref:System.Security.PermissionSet>. Vous pouvez utiliser **Assert** pour activer votre code (et les appelants en aval) pour effectuer des actions que votre code a la permission de faire, mais ses appelants pourraient ne pas avoir la permission de faire. Une assertion de sécurité modifie le processus normal de vérification de sécurité effectué par le runtime. Lors de l'assertion d'une autorisation, le système de sécurité reçoit l'ordre de ne pas vérifier que les appelants de votre code disposent de l'autorisation ayant fait l'objet d'une assertion.  
  
> [!CAUTION]
> Utilisez les assertions avec précaution, car elles peuvent ouvrir des failles de sécurité et perturber le mécanisme d'application des restrictions de sécurité du runtime.  
  
 Les assertions sont utiles quand une bibliothèque appelle du code non managé ou effectue un appel qui nécessite une autorisation qui n'est pas liée de manière évidente à l'utilisation prévue de la bibliothèque. Par exemple, tout le code géré qui appelle dans le code non géré doit avoir **SecurityPermission** avec le drapeau **UnmanagedCode** spécifié. Par défaut, le code qui ne provient pas de l'ordinateur local, comme le code téléchargé à partir de l'intranet local, ne recevra pas cette autorisation. Par conséquent, pour que le code téléchargé à partir de l'intranet local puisse appeler une bibliothèque qui utilise du code non managé, il doit disposer de l'autorisation ayant fait l'objet d'une assertion effectuée par la bibliothèque. En outre, certaines bibliothèques peuvent effectuer des appels invisibles aux appelants et nécessitent donc des autorisations spéciales.  
  
 Vous pouvez également utiliser des assertions quand votre code accède à une ressource d'une manière totalement invisible pour les appelants. Supposons, par exemple, que votre bibliothèque obtienne des informations d'une base de données, mais que, pendant le processus, elle lise également les informations du Registre de l'ordinateur. Étant donné que les développeurs qui utilisent votre bibliothèque n’ont pas accès à votre source, ils n’ont aucun moyen de savoir que leur code exige **RegistryPermission** pour utiliser votre code. Dans ce cas, si vous décidez qu'il n'est pas raisonnable ni nécessaire d'exiger que les appelants de votre code aient l'autorisation d'accéder au Registre, vous pouvez procéder à l'assertion de l'autorisation pour la lecture du Registre. Dans ce cas, il est approprié que la bibliothèque affirme la permission afin que les appelants sans **RegistrePermission** puissent utiliser la bibliothèque.  
  
 L'assertion n'affecte le parcours de pile que si l'autorisation ayant fait l'objet de l'assertion et une autorisation demandée par un appelant en aval sont de même type, et si l'autorisation demandée est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion. Par exemple, si vous affirmez **FileIOPermission** pour lire tous les fichiers sur le lecteur C, et une demande en aval est faite pour **FileIOPermission** pour lire les fichiers dans C:Temp, l’affirmation pourrait affecter la marche de pile; toutefois, si la demande était que **FileIOPermission** écrive à la commande C, l’affirmation n’aurait aucun effet.  
  
 Pour effectuer des assertions, votre code doit disposer de l'autorisation faisant l'objet de l'assertion et de <xref:System.Security.Permissions.SecurityPermission>, qui représente le droit d'effectuer des assertions. Il est possible d'effectuer une assertion pour une autorisation qui n'a pas été octroyée à votre code. Toutefois, une telle assertion serait inutile puisque la vérification de sécurité échouerait avant même que l'assertion n'ait pu faire en sorte qu'elle réussisse.  
  
 L’illustration suivante montre ce qui se passe lorsque vous utilisez **Assert**. Supposons que les instructions suivantes soient vraies concernant les assemblys A, B, C, E et F, et les deux autorisations P1 et P1A :  
  
- P1A représente le droit de lire les fichiers .txt présents sur le lecteur C.  
  
- P1 représente le droit de lire tous les fichiers présents sur le lecteur C.  
  
- P1A et P1 sont tous deux des types **fileIOPermission,** et P1A est un sous-ensemble de P1.  
  
- Les assemblys E et F ont reçu l'autorisation P1A.  
  
- L'assembly C a reçu l'autorisation P1.  
  
- Les assemblys A et B n'ont reçu ni l'autorisation P1 ni l'autorisation P1A.  
  
- La méthode A est contenue dans l'assembly A, la méthode B dans l'assembly B, et ainsi de suite.  
  
 ![Diagramme qui montre les assemblages de méthode Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 Dans ce scénario, la méthode A appelle B, B appelle C, C appelle E, et E appelle F. Méthode C affirme la permission de lire les fichiers sur le lecteur C (permission P1), et la méthode E exige la permission de lire les fichiers .txt sur le lecteur C (permission P1A). Lorsque la demande en F est rencontrée au moment de l’exécution, une promenade de pile est effectuée pour vérifier les autorisations de tous les appelants de F, à commencer par E. E a été accordé la permission P1A, de sorte que la promenade de pile procède à examiner les autorisations de C, où l’affirmation de C est découvert. Étant donné que l'autorisation demandée (P1A) est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion (P1), le parcours de pile s'arrête et la vérification de sécurité réussit automatiquement. Il n'est pas important que les assemblys A et B ne disposent pas de l'autorisation P1A. En procédant à l'assertion de P1, la méthode C garantit que ses appelants puissent accéder à la ressource protégée par P1, même s'ils n'ont pas reçu l'autorisation d'y accéder.  
  
 Si vous concevez une bibliothèque de classes et si une classe accède à une ressource protégée, vous devez, dans la plupart des cas, effectuer une demande de sécurité exigeant que les appelants de la classe possèdent l'autorisation appropriée. Si la classe effectue alors une opération pour laquelle vous savez que la plupart de ses appelants n’auront pas la permission, et si vous êtes prêt à prendre la responsabilité de laisser ces appelants appeler votre code, vous pouvez affirmer la permission en appelant la méthode **Assert** sur un objet d’autorisation qui représente l’opération que le code effectue. L’utilisation **d’Assert** de cette façon permet aux appelants qui normalement ne pouvaient pas le faire appeler votre code. Par conséquent, si vous procédez à l'assertion d'une autorisation, soyez sûr d'effectuer au préalable les vérifications de sécurité appropriées pour empêcher une utilisation abusive de votre composant.  
  
 Supposons, par exemple, que votre classe de bibliothèque hautement approuvée possède une méthode qui supprime les fichiers. Elle accède au fichier en appelant une fonction Win32 non managée. Un appelant invoque la méthode **Supprimer** de votre code, en passant au nom du fichier à supprimer, C: 'Test.txt. Dans la méthode **Supprimer,** <xref:System.Security.Permissions.FileIOPermission> votre code crée un objet représentant l’accès à C: 'Test.txt. (L’accès à la rédaction est nécessaire pour supprimer un fichier.) Votre code invoque ensuite un contrôle de sécurité impérative en appelant la méthode **de demande** de l’objet **FileIOPermission.** Si l'un des appelants de la pile des appels n'a pas cette autorisation, une <xref:System.Security.SecurityException> est levée. Si aucune exception n'est levée, vous savez que tous les appelants ont le droit d'accéder à C:\Test.txt. Parce que vous croyez que la plupart de vos appelants n’auront pas <xref:System.Security.Permissions.SecurityPermission> la permission d’accéder au code non menté, votre code crée alors un objet qui représente le droit d’appeler du code non menté et appelle la méthode **Assert** de l’objet. Enfin, il appelle la fonction non managée Win32 pour supprimer C:\Text.txt, puis retourne le contrôle à l'appelant.  
  
> [!CAUTION]
> Vous devez être sûr que votre code n'utilise pas d'assertions s'il peut être utilisé par un autre code pour accéder à une ressource protégée par l'autorisation faisant l'objet de l'assertion. Par exemple, dans le code qui écrit à un fichier dont le nom est spécifié par l’appelant comme paramètre, vous n’affirmeriez pas le **FileIOPermission** pour écrire à des fichiers parce que votre code serait ouvert à une utilisation abusive par un tiers.  
  
 Lorsque vous utilisez la syntaxe de sécurité impérative, appeler la méthode **Assert** sur plusieurs autorisations dans la même méthode provoque une exception de sécurité à jeter. Au lieu de cela, vous devez créer un objet **PermissionSet,** lui passer les autorisations individuelles que vous souhaitez invoquer, puis appeler la méthode **Assert** sur **l’objet PermissionSet.** Vous pouvez appeler la méthode **Assert** plus d’une fois lorsque vous utilisez la syntaxe de sécurité déclarative.  
  
 L’exemple suivant montre la syntaxe déclarative pour les contrôles de sécurité prépondérants à l’aide de la méthode **Assert.** Notez que la syntaxe **FileIOPermissionAttribute** tient deux valeurs : un <xref:System.Security.Permissions.SecurityAction> recensement et l’emplacement du fichier ou de l’annuaire auquel l’autorisation doit être accordée. L’appel à **Assert** provoque `C:\Log.txt` des demandes d’accès à la réussite, même si les appelants ne sont pas vérifiés pour la permission d’accéder au fichier.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}
```  
  
 Les fragments de code suivants montrent une syntaxe impérative pour les contrôles de sécurité prépondéraux à l’aide de la méthode **Assert.** Dans cet exemple, un cas de l’objet **FileIOPermission** est déclaré. Son constructeur est adopté **FileIOPermissionAccess.AllAccess** pour définir le type d’accès autorisé, suivi d’une chaîne décrivant l’emplacement du fichier. Une fois **l’objet FileIOPermission** défini, vous n’avez qu’à appeler sa méthode **Assert** pour passer outre au contrôle de sécurité.  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Attributs](../../standard/attributes/index.md)
- [Sécurité d’accès au code](code-access-security.md)
