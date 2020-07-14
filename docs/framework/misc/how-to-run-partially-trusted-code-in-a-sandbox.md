---
title: "Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable (sandbox)"
description: Découvrez comment exécuter du code partiellement fiable dans un bac à sable (sandbox) dans .NET. La classe AppDomain est un moyen efficace de Sandboxer les applications managées.
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: 4f186f1d901b51dd4c61ba6b22197465a41f2c44
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282032"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable (sandbox)
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 L'utilisation de bac à sable (sandbox) consiste à exécuter du code dans un environnement de sécurité restreint qui limite les autorisations d'accès accordées au code. Par exemple, si une bibliothèque managée provient d'une source qui n'est pas totalement fiable, vous ne devez pas l'exécuter comme ayant un niveau de confiance totale. Au lieu de cela, placez le code dans un bac à sable (sandbox) qui limite ses autorisations à ceux qui en ont besoin (par exemple, l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>).  
  
 Vous pouvez également utiliser un bac à sable (sandbox) pour tester le code pour tester du code à distribuer qui s'exécute dans des environnements partiellement fiables.  
  
 Un <xref:System.AppDomain> est un moyen efficace de fournir un bac à sable (sandbox) pour les applications managées. Les domaines d'application utilisés pour l'exécution du code de niveau de confiance partiel disposent d'autorisations qui définissent les ressources protégées disponibles au moment de l'exécution dans ce <xref:System.AppDomain>. Le code qui s'exécute à l'intérieur du <xref:System.AppDomain> est lié au <xref:System.AppDomain> par les autorisations qui lui sont associées et est autorisé à accéder uniquement aux ressources spécifiées. Le <xref:System.AppDomain> inclut également un tableau <xref:System.Security.Policy.StrongName> utilisé pour identifier les assemblys qui seront chargés avec un niveau de confiance totale. Cela permet au concepteur d'un <xref:System.AppDomain> de démarrer un nouveau domaine bac à sable (sandbox) qui permet aux assemblys d'assistance spécifiques d'avoir un niveau de confiance totale. Une autre option pour le chargement d'assemblys avec un niveau de confiance totale est de les placer dans le Global Assembly Cache ; toutefois, cela les charge avec un niveau de confiance totale dans tous les domaines d'application créés sur l'ordinateur. La liste des noms forts prend en charge une décision pour chaque <xref:System.AppDomain> qui fournit une détermination plus restrictive.  
  
 Vous pouvez utiliser la surcharge de la méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> pour définir le jeu d'autorisations des applications qui s'exécutent dans un bac à sable (sandbox). Cette surcharge vous permet de spécifier le niveau de sécurité d'accès du code exact que vous souhaitez. Les assemblys chargés dans un <xref:System.AppDomain> à l'aide de cette surcharge peuvent disposer soit uniquement du jeu d'autorisations spécifié, soit de la confiance totale. La confiance totale est accordée à l'assembly s'il se trouve dans le Global Assembly Cache ou est répertorié dans le paramètre de tableau `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>). Seuls les assemblys réputés être entièrement fiables doivent être ajoutés à la liste `fullTrustAssemblies`.  
  
 La surcharge possède la signature suivante :  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Les paramètres de la surcharge de méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> spécifient le nom du <xref:System.AppDomain>, la preuve du <xref:System.AppDomain>, l'objet <xref:System.AppDomainSetup> qui identifie la base de l'application pour le bac à sable (sandbox), le jeu d'autorisations à utiliser et les noms forts des assemblys entièrement fiables.  
  
 Pour des raisons de sécurité, la base de l'application définie dans le paramètre `info` ne doit pas être la base de l'application pour l'application d'hébergement.  
  
 Pour le paramètre `grantSet`, vous pouvez spécifier un jeu d'autorisations que vous avez explicitement créé ou un jeu d'autorisations standard créé par la méthode <xref:System.Security.SecurityManager.GetStandardSandbox%2A>.  
  
 Contrairement à la plupart des surcharges <xref:System.AppDomain>, la preuve pour le <xref:System.AppDomain> (fournie par le paramètre `securityInfo`) n'est pas utilisée pour déterminer le jeu d'autorisations pour les assemblys partiellement fiables. Elle est en fait spécifiée indépendamment par le paramètre `grantSet`. Toutefois, la preuve peut être utilisée à d'autres fins, par exemple, pour déterminer la portée de stockage isolé.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Pour exécuter une application dans un bac à sable (sandbox)  
  
1. Créez le jeu d'autorisations à accorder à l'application non fiable. L'autorisation minimale que vous pouvez accorder est l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>. Vous pouvez également accorder des autorisations supplémentaires que vous pensez sécurisées pour du code non fiable ; par exemple, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Le code suivant crée un jeu d'autorisations uniquement avec l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Vous pouvez également utiliser un jeu d'autorisations nommé existant, tel qu'Internet.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     En fonction de la zone dans la preuve, la méthode <xref:System.Security.SecurityManager.GetStandardSandbox%2A> retourne un jeu d'autorisations `Internet` ou un jeu d'autorisations `LocalIntranet`. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> construit également des autorisations d'identité pour certains objets de preuve passés comme références.  
  
2. Signez l'assembly qui contient la classe d'hébergement (appelée `Sandboxer` dans cet exemple) qui appelle le code non fiable. Ajouter le <xref:System.Security.Policy.StrongName> utilisé pour signer l'assembly au tableau <xref:System.Security.Policy.StrongName> du paramètre `fullTrustAssemblies` paramètre de l'appel <xref:System.AppDomain.CreateDomain%2A>. La classe d'hébergement doit être exécutée avec un niveau de confiance totale pour permettre l'exécution du code de confiance partielle ou offrir des services à l'application de confiance partielle. Voici comment lire le <xref:System.Security.Policy.StrongName> d'un assembly :  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Les assemblys .NET Framework tels que mscorlib et System.dll n'ont pas à être ajoutés à la liste de confiance totale, car ils sont chargés avec un niveau de confiance totale à partir du Global Assembly Cache.  
  
3. Initialisez le paramètre <xref:System.AppDomainSetup> de la méthode <xref:System.AppDomain.CreateDomain%2A>. Ce paramètre vous permet de contrôler la plupart des paramètres du nouveau <xref:System.AppDomain>. La propriété <xref:System.AppDomainSetup.ApplicationBase%2A> est un paramètre important qui doit être différent de la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> pour le <xref:System.AppDomain> de l'application d'hébergement. Si les paramètres <xref:System.AppDomainSetup.ApplicationBase%2A> sont les mêmes, l'application de confiance partielle peut amener l'application d'hébergement à charger (avec un niveau de confiance totale) une exception définie par ses soins, et donc l'exploiter. Cela fait partie des raisons pour lesquelles un Catch (exception) n'est pas recommandé. En configurant la base d'application de l'hôte différemment de la base d'application de l'application bac à sable (sandbox), vous réduisez les risques d'attaques.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Appelez la surcharge de méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> pour créer le domaine d'application à l'aide des paramètres spécifiés.  
  
     La signature de cette méthode est :  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informations complémentaires :  
  
    - Il s'agit de la seule surcharge de la méthode <xref:System.AppDomain.CreateDomain%2A> prenant un <xref:System.Security.PermissionSet> comme paramètre, et donc la seule surcharge qui vous permet de charger une application dans un paramètre de confiance partielle.  
  
    - Le paramètre `evidence` n'est pas utilisé pour calculer un jeu d'autorisations, mais pour être identifié par les autres fonctionnalités du .NET Framework.  
  
    - La définition de la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> du paramètre `info` est obligatoire pour cette surcharge.  
  
    - Le paramètre `fullTrustAssemblies` possède le mot clé `params`, ce qui signifie qu'il n'est pas nécessaire de créer un tableau <xref:System.Security.Policy.StrongName>. Passer 0, 1 ou plusieurs noms forts comme paramètres est autorisé.  
  
    - Le code servant à créer le domaine d'application est le suivant :  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Chargez le code dans le <xref:System.AppDomain> bac à sable (sandbox) que vous avez créé. Cette opération peut être réalisée de deux manières :  
  
    - Appelez la méthode <xref:System.AppDomain.ExecuteAssembly%2A> pour l'assembly.  
  
    - Utilisez la méthode <xref:System.Activator.CreateInstanceFrom%2A> pour créer une instance d'une classe dérivée de <xref:System.MarshalByRefObject> dans le nouveau <xref:System.AppDomain>.  
  
     La seconde méthode est préférable, car elle simplifie le passage des paramètres à la nouvelle instance <xref:System.AppDomain>. La méthode <xref:System.Activator.CreateInstanceFrom%2A> fournit deux fonctionnalités importantes :  
  
    - Vous pouvez utiliser une base de code qui pointe vers un emplacement qui ne contient pas votre assembly.  
  
    - Vous pouvez effectuer la création sous un <xref:System.Security.CodeAccessPermission.Assert%2A> pour la confiance totale (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), ce qui vous permet de créer une instance d'une classe critique. (Cela se produit chaque fois que votre assembly n’a pas de marquages de transparence et qu’il est chargé avec un niveau de confiance totale.) Par conséquent, vous devez veiller à créer uniquement le code que vous approuvez avec cette fonction, et nous vous recommandons de créer uniquement des instances de classes de confiance totale dans le nouveau domaine d’application.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Notez que pour créer une instance d'une classe dans un nouveau domaine, cette classe doit étendre la classe <xref:System.MarshalByRefObject>.  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Désencapsulez la nouvelle instance de domaine dans une référence de ce domaine. Cette référence est utilisée pour exécuter le code non fiable.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Appelez la méthode `ExecuteUntrustedCode` dans l'instance de la classe `Sandboxer` que vous venez de créer.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Cet appel est exécuté dans le domaine d'application bac à sable (sandbox), qui possède des autorisations restreintes.  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection> est utilisé pour obtenir le handle d'une méthode dans l'assembly de niveau de confiance partielle. Le handle permet d'exécuter du code d'une façon sécurisée avec les autorisations minimales.  
  
     Dans le code précédent, notez <xref:System.Security.PermissionSet.Assert%2A> pour l'autorisation de confiance totale avant l'affichage de <xref:System.Security.SecurityException>.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     L'assertion de confiance totale permet d'obtenir les informations détaillées de <xref:System.Security.SecurityException>. Sans <xref:System.Security.PermissionSet.Assert%2A>, la méthode <xref:System.Security.SecurityException.ToString%2A> de <xref:System.Security.SecurityException> détecte que du code de niveau de confiance partielle se trouve sur la pile et restreint les informations retournées. Cela peut provoquer des problèmes de sécurité si le code de confiance partielle peut lire ces informations. Cependant, le risque est atténué par le fait de ne pas accorder <xref:System.Security.Permissions.UIPermission>. L'assertion de confiance totale doit être utilisée avec modération et uniquement quand vous êtes sûr de ne pas autoriser du code à passer du niveau de confiance partielle au niveau de confiance totale. En règle générale, n'appelez pas de code non fiable dans la même fonction et après avoir appelé une assertion de confiance totale. Nous vous conseillons de toujours rétablir l'assertion quand vous avez terminé de l'utiliser.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant implémente la procédure de la section précédente. Dans l'exemple, un projet nommé `Sandboxer` dans une solution Visual Studio contient également un projet nommé `UntrustedCode`, qui implémente la classe `UntrustedClass`. Ce scénario suppose que vous avez téléchargé un assembly de bibliothèque qui contient une méthode censée retourner la valeur `true` ou `false` pour indiquer si le nombre que vous avez fourni est un nombre de Fibonacci. À la place, la méthode essaie de lire un fichier de votre ordinateur. L'exemple suivant illustre le code non fiable.  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 L'exemple suivant montre le code de l'application `Sandboxer` qui exécute le code non fiable.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
