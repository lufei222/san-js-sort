# sanUtils

前端实现多条件排序
demo：
----------------------------------------
    /**
     * 初始化排序参数 0：排序算法，-1：降序，2：升序
     */
    function initSortField(){
        sortField.category=0;
        sortField.designation=1;//默认升序
        sortField.manufacturer=0;
        sortField.city=0;
        sortField.current=0;
        sortField.diff =0;
        sortField.buyerPrice=0;
        sortField.buyerWeight=-1;
        sortField.sellerPrice=0;
        sortField.sellerWeight=-1;
        sortField.dealtWeight=-1;
    }
    
    ----------------------------------------

    /**
     * 排序算法
     * @param data
     * @returns {*}
     */
    function sortListByField(data){//字段排序
        var quotationList=data.products
        quotationList.sort(
             firstBy(sortField.dealtWeight==0?"":"dealtWeight", {ignoreCase:true, direction:sortField.dealtWeight})//firstBy：direction: -1:desc▽, 1:asc△
            .thenBy(sortField.sellerWeight==0?"":"sellerWeight",sortField.sellerWeight)
            .thenBy(sortField.buyerWeight==0?"":"buyerWeight",sortField.buyerWeight)
            .thenBy(sortField.designation==0?"":"designation",sortField.designation)
            .thenBy(sortField.category==0?"":"category",sortField.category)
            .thenBy(sortField.manufacturer==0?"":"manufacturer",sortField.manufacturer)
            .thenBy(sortField.current==0?"":"current",sortField.current)
            .thenBy(sortField.buyerPrice==0?"":"buyerPrice",sortField.buyerPrice)
            .thenBy(sortField.sellerPrice==0?"":"sellerPrice",sortField.sellerPrice)
            .thenBy(sortField.city==0?"":"city",sortField.city)
            .thenBy(sortField.diff==0?"":"diff",sortField.diff)
        )
