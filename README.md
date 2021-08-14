# rutranslit
Python-модуль написанный на Rust. Предназначен для выполнения замены символов в строке (транслит)

Модуль __rutranslit.pyd__

Содержит 2 функции:

  def _translit(text: str, table: Dict[str, str]) -> str_;
  
    На основании переданного текста формирует новую строку, выполняя замену символов в соответствии с переданным table;
    (table в качестве key должен содержать str с одним символом(!), value - произвольный str);
     Символы, которые в словаре table не были найдены, остаются без изменения.
    
  def _translit_text_kir_to_lat(text: str) -> str_;
  
    Выполняет замену символов кириллицы на латиницу с использованием функции translit и 
    таблицы соответствия ГОСТ Р 7.0.34-2014 (упрощенная);
    
Пример:
``` Python  
import rutranslit



if __name__ == "__main__":
    text = "Чебурашка"
    
    tab = {
        'Ч': 'CH',
        'б': "b", 
    }

    print(rutranslit.translit(text, tab)) # CHеbурашка
    print(rutranslit.translit_text_kir_to_lat(text)) # CHeburashka
```



