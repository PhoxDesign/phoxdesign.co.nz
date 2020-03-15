---
layout: post
title: Repeater and paging in asp.net (previous and next style)
categories: asp
---


Most people use repeater in web projects and paging is always trouble for us. You never create paging which is in your minds. I was using collectionpager but there is to many numbers in my page for paging. like: 1-2-3-4-5-6-7-8-..... goes on. And collectionpager is not good enough. So I tried listview and datapager but it was not work correctly. In this example we make our paging style like wordpress classic paging method. (Older-Newer Posts)
 
html side:
< div style="float:left; margin-right:20px;">< /asp:LinkButton>< /div>
< div style="float:left;">< /asp:LinkButton>< /div>
 
// and you also have a repeater, datalist ...etc
 
codebehind:
    #region like wp older post - newer post
 
    PagedDataSource objPds = new PagedDataSource();
    objPds.DataSource = dtArticles.DefaultView;
    objPds.AllowPaging = true;
    objPds.PageSize = 7;
 
    // Request.Querystring["page"].ToString();
    //I couldn't take page number with querystring I don't know why, anyway...
 
    string myPage = Request.Params.Get("page");
 
    if (myPage != null && myPage != "")
       objPds.CurrentPageIndex = Convert.ToInt32(myPage);
 
    if (objPds.IsFirstPage)
       lnkPrev.Visible = false;
    if (objPds.IsLastPage)
       lnkNext.Visible = false;
 
    rptArticles.DataSource = objPds;
    rptArticles.DataBind();
 
    #endregion
 
    protected void lnkPrev_Click(object sender, EventArgs e)
    {
        int myPage = Convert.ToInt32(Request.Params.Get("page"));
        myPage -= 1;
        Response.Redirect("default.aspx?page=" + myPage);
    }
 
    protected void lnkNext_Click(object sender, EventArgs e)
    {
        int myPage = Convert.ToInt32(Request.Params.Get("page"));
        myPage += 1;
        Response.Redirect("default.aspx?page=" + myPage);
    }

