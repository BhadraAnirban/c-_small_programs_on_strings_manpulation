# c-_small_programs_on_strings_manpulation


```
[HttpGet("test")]
        public ActionResult Test(string input)
        {
            var hasUnderscore = input.Contains("_");
            StringBuilder result = new StringBuilder();
            if (hasUnderscore)
            {
                var hasfacedUnderscore = false;
                
                foreach(var ch in input)
                {
                    if(hasfacedUnderscore && !ch.Equals('_'))
                    {
                        result.Append(char.ToUpper(ch));
                        hasfacedUnderscore = false;
                    }
                    else if(!ch.Equals('_'))
                    {
                        result.Append(ch);
                    }
                    else if(ch.Equals('_'))
                    {
                        hasfacedUnderscore = true;
                    }
                }
                
            }
            else
            {
                foreach (var ch in input)
                {
                    if(char.IsUpper(ch))
                    {
                        result.Append('_').Append(char.ToLower(ch));
                    }
                    else
                    {
                        result.Append(ch);
                    }
                }
            }
            return Ok(result.ToString());
        }
        
/// <summary>
        /// Convert '_' related variable to Upper and viceversa
        /// p_mkj_ki_jay => pMkjKiJay
        /// pMkjKiJay => p_mkj_ki_jay
        /// </summary>
        /// <param name="input"></param>
        /// <returns></returns>
        [HttpGet("test3")]
        public ActionResult Test3(string input)
        {
            var hasUnderscore = input.Contains("_");
            StringBuilder result = new StringBuilder();
            if (hasUnderscore)
            {
                var hasfacedUnderscore = false;

                foreach (var ch in input)
                {
                    if (hasfacedUnderscore && !ch.Equals('_'))
                    {
                        result.Append(char.ToUpper(ch));
                        hasfacedUnderscore = false;
                    }
                    else if (!ch.Equals('_'))
                    {
                        result.Append(ch);
                    }
                    else if (ch.Equals('_'))
                    {
                        hasfacedUnderscore = true;
                    }
                }

            }
            else
            {
                foreach (var ch in input)
                {
                    if (char.IsUpper(ch))
                    {
                        result.Append('_').Append(char.ToLower(ch));
                    }
                    else
                    {
                        result.Append(ch);
                    }
                }
            }
            return Ok(result.ToString());
        }

        /// <summary>
        /// Sort and count number of characters in a string
        /// Approved pmkjkijay => a1i1j2k2m1p1y1
        /// </summary>
        /// <param name="input"></param>
        /// <returns></returns>
        [HttpGet("test2")]  
        public ActionResult Test2(string input)
        {
            StringBuilder result = new StringBuilder();
            SortedList<char, int> objList = new SortedList<char, int>();

            foreach (var cha in input)
            {
                var exist = objList.ContainsKey(cha);
                if (!exist)
                {
                    objList.Add(cha, 1);
                }
                else
                {
                    objList[cha] = objList[cha] + 1;
                }
            }
            
            foreach (var oo in objList)
            {
                result = result.Append(oo.Key).Append(oo.Value);
            }
            return Ok(result.ToString());
        }

        /// <summary>
        ///  ///// pmkjkijay => a1i1j2k2m1p1y1
        /// </summary>
        /// <param name="input"></param>
        /// <returns></returns>
        [HttpGet("test1")]
        public ActionResult Test1(string input)
        {
            StringBuilder result = new StringBuilder();
            List<Obj> objList = new List<Obj>();

            foreach (var cha in input)
            {
                var exist = objList.SingleOrDefault(p => p.data == cha);
                if (exist == null)
                {
                    var newobj = new Obj(cha);
                    objList.Add(newobj);
                }
                else
                {
                    ++exist.count;
                }
            }
            objList = objList.OrderBy(p => p.data).ToList();
            foreach (var oo in objList)
            {
                result = result.Append(oo.data).Append(oo.count);
            }
            return Ok(result.ToString());
        }

```
```
public class Obj{
        public Obj(char d)
        {
            data = d;
            count = 1;
        }
        public int count { get; set; }
        public char data { get; set; }
    }
```
