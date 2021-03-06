---
title: 'Procédure : lier le contrôle DataGrid Windows Forms à une source de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: bac24c2dd622ea780408e902d08708ac09561044
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922723"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Procédure : lier le contrôle DataGrid Windows Forms à une source de données
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms est spécifiquement conçu pour afficher des informations à partir d’une source de données. Vous liez le contrôle au moment de l’exécution en <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> appelant la méthode. Bien que vous puissiez afficher des données provenant de diverses sources de données, les sources les plus courantes sont les jeux de données et les vues de données.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Pour lier des données au contrôle DataGrid par programmation  
  
1. Écrivez du code pour remplir le DataSet.  
  
     Si la source de données est un DataSet ou une vue de données basée sur une table de DataSet, ajoutez du code au formulaire pour remplir le DataSet.  
  
     Le code exact que vous utilisez dépend de l’emplacement où le jeu de données obtient des données. Si le DataSet est rempli directement à partir d’une base de données, vous `Fill` appelez généralement la méthode d’un adaptateur de données, comme dans l’exemple suivant, qui remplit `DsCategories1`un DataSet appelé:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Si le jeu de données est rempli à partir d’un service Web XML, vous créez généralement une instance du service dans votre code, puis vous appelez l’une de ses méthodes pour retourner un jeu de données. Vous fusionnez ensuite le jeu de données du service Web XML dans votre jeu de données local. L’exemple suivant montre comment vous pouvez créer une instance d’un service Web XML appelé `CategoriesService`, appeler sa `GetCategories` méthode et fusionner le jeu de données résultant dans un jeu `DsCategories1`de données local appelé:  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. Appelez la <xref:System.Windows.Forms.DataGrid> méthode du <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> contrôle, en lui transmettant la source de données et un membre de données. Si vous n’avez pas besoin de passer explicitement un membre de données, transmettez une chaîne vide.  
  
    > [!NOTE]
    > Si vous liez la grille pour la première fois, vous pouvez définir les propriétés et <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> du contrôle. Toutefois, vous ne pouvez pas réinitialiser ces propriétés une fois qu’elles ont été définies. Par conséquent, il est recommandé de toujours utiliser la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode.  
  
     L’exemple suivant montre comment vous pouvez lier par programmation à la table Customers dans un DataSet appelé `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Si la table Customers est la seule table dans le jeu de données, vous pouvez également lier la grille de cette façon:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. Facultatif Ajoutez les styles de table et de colonne appropriés à la grille. S’il n’existe aucun style de table, vous verrez la table, mais avec une mise en forme minimale et une fois toutes les colonnes visibles.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [Guide pratique pour Ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
