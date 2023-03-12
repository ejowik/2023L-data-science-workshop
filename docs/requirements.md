### Wymagania odnośnie modelu:

Model ma umożliwiając wykrywanie obiektów z użyciem frameworku YOLOX https://github.com/Megvii-BaseDetection/YOLOX

Model ma wspierać wykrywanie następujących klas obiektów:
1. person (osoba)
2. helmet (kask)
3. head (głowa)
4. vest (kamizelka odblaskowa)

zapewniając:
1. Jak najlepsze unikanie wykrywania przypadków false positive (np osób łysych lub osób w czapce z daszkiem)
2. Model ma dac się uruchomić z użyciem framework YOLOX (fianlne testy będą z uzyciem framework’u Orange)
3. Wsparcie dla modelu YOLOX "S" https://github.com/Megvii-BaseDetection/YOLOX/blob/main/exps/default/yolox_s.py 
4. Model ma działać z dokładnością (Accurancy) min 95%

### Deliverables
1. Model w formatach: onnx oraz natywych dla yolox (bin i xml)
2. Zbiory danych uczący i testowy
3. Wyniki testów min zawierające czułość R (ang. Recall), precyzję P (ang. Precision) i dokładność A (ang. Accuracy) algortymu dla poszczególnych klas obiektów
4. Instrukcja opisująca kroki potrzebne do stworzenia i przetestowania modelu


### Przydatne dokumentacja i instrukcje:
1. https://www.forecr.io/blogs/ai-algorithms/how-to-train-a-custom-object-detection-model-with-yolox
2. https://javamana.com/2022/03/202203170640154681.html
3. https://yolox.readthedocs.io/en/latest/demo/onnx_readme.html
