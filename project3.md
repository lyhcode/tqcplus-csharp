# 第三類

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace CSD03
{
    class Program
    {
        static void Main(string[] args)
        {
            IEnumerable<ProductDataItem> productDataItems = ProductData.GetData();
            IEnumerable<StockDataItem> stockDataItems = StockData.GetData();

            // TODO: write LINQ statements and output result.
            // TODO: must use Lambda Expression to handle condition.
            ////where (p.Cost * s.Stock) >= 250000

            var query = from p in productDataItems
                        join s in stockDataItems
                        on p.ProductID equals s.ProductID
                        select new
                        {
                            id = p.ProductID,
                            cost = p.Cost,
                            stock = s.Stock
                        };


            var query2 = query.Where(row => (row.cost * row.stock) >= 250000);
            
            foreach (var result in query2)
            {
                Console.WriteLine("Product id: {0}, cost: {1}, stock: {2}, total: {3}",
                    result.id, result.cost, result.stock, result.cost * result.stock);
            }

            Console.ReadLine();
        }
    }
}

```