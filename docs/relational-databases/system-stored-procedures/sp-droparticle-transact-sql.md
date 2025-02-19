---
description: "sp_droparticle (Transact-SQL)"
title: "sp_droparticle (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: sql
ms.prod_service: "database-engine"
ms.reviewer: ""
ms.technology: replication
ms.topic: "reference"
dev_langs: 
  - "TSQL"
f1_keywords: 
  - "sp_droparticle_TSQL"
  - "sp_droparticle"
helpviewer_keywords: 
  - "sp_droparticle"
ms.assetid: 09fec594-53f4-48a5-8edb-c50731c7adb2
author: markingmyname
ms.author: maghan
---
# sp_droparticle (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Drops an article from a snapshot or transactional publication. An article cannot be removed if one or more subscriptions to it exist. This stored procedure is executed at the Publisher on the publication database.  
  
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```  
  
sp_droparticle [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @from_drop_publication = ] from_drop_publication ]  
```  
  
## Arguments  
`[ @publication = ] 'publication'`
 Is the name of the publication that contains the article to be dropped. *publication* is **sysname**, with no default.  
  
`[ @article = ] 'article'`
 Is the name of the article to be dropped. *article* is **sysname**, with no default.  
  
`[ @ignore_distributor = ] ignore_distributor`
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`
 Acknowledges that the action taken by this stored procedure may invalidate an existing snapshot. *force_invalidate_snapshot* is a **bit**, with a default of **0**.  
  
 **0** specifies that changes to the article do not cause the snapshot to be invalid. If the stored procedure detects that the change does require a new snapshot, an error occurs and no changes are made.  
  
 **1** specifies that changes to the article may cause the snapshot to be invalid, and if there are existing subscriptions that would require a new snapshot, gives permission for the existing snapshot to be marked as obsolete and a new snapshot generated.  
  
`[ @publisher = ] 'publisher'`
 Specifies a non- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher. *publisher* is **sysname**, with a default of NULL.  
  
> [!NOTE]  
>  *publisher* should not be used when changing article properties on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.  
  
`[ @from_drop_publication = ] from_drop_publication`
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## Return Code Values  
 **0** (success) or **1** (failure)  
  
## Remarks  
 **sp_droparticle** is used in snapshot and transactional replication.  
  
 For horizontally filtered articles, **sp_droparticle** checks the **type** column of the article in the [sysarticles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md) table to determine whether a view or filter should also be dropped. If a view or filter was autogenerated, it is dropped with the article. If it was manually created, it is not dropped.  
  
 Executing **sp_droparticle** to drop an article from a publication does not remove the object from the publication database or the corresponding object from the subscription database. Use `DROP <object>` to manually remove these objects if necessary.  
  
## Example  
 [!code-sql[HowTo#sp_droparticle](../../relational-databases/replication/codesnippet/tsql/sp-droparticle-transact-_1.sql)]  
  
## Permissions  
 Only members of the **sysadmin** fixed server role or **db_owner** fixed database role can execute **sp_droparticle**.  
  
## See Also  
 [Delete an Article](../../relational-databases/replication/publish/delete-an-article.md)   
 [Add Articles to and Drop Articles from Existing Publications](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Replication Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
