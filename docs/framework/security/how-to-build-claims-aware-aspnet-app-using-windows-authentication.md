---
title: 'Procédure : Générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 34d6c7916b3035e9896b1dd9d7c7d8b3e7b0fcfc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040998"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Procédure : Générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification Windows

## <a name="applies-to"></a>S'applique à

- Microsoft® Windows® Identity Foundation (WIF)

- Web Forms ASP.NET®

## <a name="summary"></a>Récapitulatif

Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application Web Forms ASP.NET prenant en charge les revendications et qui utilise l’authentification Windows. Elle fournit également des instructions pour tester l’application afin de vérifier que les revendications s’affichent quand un utilisateur se connecte à l’aide de l’authentification Windows.

## <a name="contents"></a>Sommaire

- Objectifs

- Présentation

- Résumé des étapes

- Étape 1 : Créer une application Web Forms ASP.NET simple

- Étape 2 : configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows

- Étape 3 : tester votre solution

## <a name="objectives"></a>Objectifs

- Configurer une application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows

- Tester l’application Web Forms ASP.NET pour vérifier si elle fonctionne correctement

## <a name="overview"></a>Présentation

Dans .NET 4.5, WIF et son autorisation basée sur les revendications ont été ajoutés en tant que partie intégrante du .NET Framework. Auparavant, si vous vouliez obtenir des revendications d’un utilisateur ASP.NET, vous deviez installer WIF et convertir les interfaces en objets Entité de sécurité tels que `Thread.CurrentPrincipal` ou `HttpContext.Current.User`. À présent, les revendications sont prises en charge automatiquement par ces objets Entité de sécurité.

L’authentification Windows a bénéficié de l’ajout de WIF dans .NET 4.5, car tous les utilisateurs authentifiés par les informations d’identification Windows sont automatiquement associés à des revendications. Vous pouvez commencer à utiliser ces revendications immédiatement dans une application ASP.NET qui utilise l’authentification Windows, comme l’illustre cette procédure.

## <a name="summary-of-steps"></a>Résumé des étapes

- Étape 1 : Créer une application Web Forms ASP.NET simple

- Étape 2 : configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows

- Étape 3 : tester votre solution

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Étape 1 : Créer une application Web Forms ASP.NET simple

Lors de cette étape, vous allez créer une application Web Forms ASP.NET.

### <a name="to-create-a-simple-aspnet-application"></a>Pour créer une application ASP.NET simple

1. Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.

2. Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.

3. Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.

4. Une fois le projet **TestApp** créé, cliquez dessus dans l’**Explorateur de solutions**. Les propriétés du projet s’affichent dans le volet **Propriétés** sous l’**Explorateur de solutions**. Affectez à la propriété **Authentification Windows** la valeur **Enabled** (Activée).

    > [!WARNING]
    > L’authentification Windows étant désactivée par défaut dans les nouvelles applications ASP.NET, vous devez l’activer manuellement.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Étape 2 : configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows

Dans cette étape, vous allez ajouter une entrée de configuration au fichier de configuration *Web.config* et modifier le fichier *Default.aspx* pour afficher les informations sur les revendications d’un compte.

### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Pour configurer une application ASP.NET pour les revendications à l’aide de l’authentification Windows

1. Dans le fichier *Default.aspx* du projet **TestApp**, remplacez le balisage existant par le suivant :

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Windows authenticated user.
        </p>
        <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

    Cette étape ajoute un contrôle GridView à votre page *Default.aspx* qui sera remplie avec les revendications récupérées à partir de l’authentification Windows.

2. Enregistrez le fichier *Default.aspx*, puis ouvrez son fichier code-behind nommé *Default.aspx.cs*. Remplacez le code existant par le code ci-dessous :

    ```csharp
    using System;
    using System.Web.UI;
    using System.Security.Claims;

    namespace TestApp
    {
        public partial class _Default : Page
        {
            protected void Page_Load(object sender, EventArgs e)
            {
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                this.ClaimsGridView.DataBind();
            }
        }
    }
    ```

    Le code ci-dessus affiche les revendications relatives à un utilisateur authentifié.

3. Pour modifier le type d’authentification de l’application, modifiez le bloc **\<authentication>** dans la section **\<system.web>** du fichier *Web.config* de la racine du projet afin d’inclure uniquement l’entrée de configuration suivante :

    ```xml
    <authentication mode="Windows" />
    ```

4. Enfin, modifiez le bloc **\<authorization>** dans la section **\<system.web>** du même fichier *Web.config* pour forcer l’authentification :

    ```xml
    <authorization>
        <deny users="?" />
    </authorization>
    ```

## <a name="step-3--test-your-solution"></a>Étape 3 : tester votre solution

Dans cette étape, vous allez tester votre application Web Forms ASP.NET et vérifier que les revendications s’affichent quand un utilisateur se connecte à l’aide de l’authentification Windows.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Pour tester votre application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows

1. Appuyez sur **F5** pour générer et exécuter l’application. La page *Default.aspx* doit s’afficher, avec le nom de votre compte Windows (dont le nom de domaine) comme utilisateur authentifié dans la partie supérieure droite de la page. Le contenu de la page doit inclure un tableau rempli avec les revendications récupérées à partir de votre compte Windows.
