import zipfile 
import os
import datetime

def myFilezip():
	today = datetime.datetime.now()
	today = today.strftime('%d_%m_%Y')	
	newzip=zipfile.ZipFile("D:\\bias\\" + today + ".rar", "w") #создаем архив
	for folder, subfolders, files in os.walk('D:\\bias'):  #поиск всех файлов в каталоге
		for file in files:
			if file.endswith('.docx') or file.endswith('.doc'):
				newzip.write(os.path.join(folder, file), os.path.relpath(os.path.join(folder,file), 'D:\\bias'), compress_type = zipfile.ZIP_DEFLATED)


	newzip.close() #закрываем архив
	
myFilezip()
