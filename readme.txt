public class Dataprovider {
	public static String[][] getexceldata() {
	String filelocation="C:\\Users\\ARUN\\OneDrive\\Documents\\poiletcode.xlsx";
	XSSFWorkbook workbook = null;
	try {
		workbook = new XSSFWorkbook(filelocation);
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
	XSSFSheet sheet=workbook.getSheetAt(0);
	int lastRowNum=sheet.getLastRowNum();
	int PhysicalNumberOfRows=sheet.getPhysicalNumberOfRows();
	short LastCellNum=sheet.getRow(0).getLastCellNum();
	String[][] data=new String[lastRowNum][LastCellNum];
	for(int i = 1;i<lastRowNum;i++) {
		XSSFRow row=sheet.getRow(i);
		for(int j=0;j<LastCellNum;j++) {
			XSSFCell cell= row.getCell(j);
			DataFormatter x=new DataFormatter();
			String value=	x.formatCellValue(cell);
			data[i-1][j]=value;
		}
	}
	try {
		workbook.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
	return data;
}
}
