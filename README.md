# Rshiny_DT
Rshiny解决DT包不显示问题


在使用DT包进行Rshiny进行显示表格的时候会一直弹不出表格来，解决方法如下：

在UI中使用：

                           box(
                             title=tagList(shiny::icon("list-alt"),"结果"),solidHeader=T,width=12,
                             collapsible=T,DT::dataTableOutput("plot24")
                           ))
在server中使用：

                            output$plot24 <- DT::renderDataTable({

                              it1 <- as.data.frame(it1)

                              DT::datatable(it1)

                            })
其中都在DT的函数前添加了DT，因为Rshiny绘制表格的包除了DT外还有其他几个包，会产生函数同名冲突。上述办法很好解决了这个bug！
