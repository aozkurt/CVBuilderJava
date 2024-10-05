import com.itextpdf.io.font.constants.StandardFonts;
import com.itextpdf.io.image.ImageData;
import com.itextpdf.kernel.pdf.PdfDocument;
import com.itextpdf.kernel.pdf.PdfWriter;
import com.itextpdf.layout.Document;
import com.itextpdf.layout.element.Paragraph;
import com.itextpdf.io.image.ImageDataFactory;
import com.itextpdf.kernel.colors.Color;
import com.itextpdf.kernel.colors.ColorConstants;
import com.itextpdf.kernel.font.PdfFont;
import com.itextpdf.kernel.font.PdfFontFactory;
import com.itextpdf.kernel.pdf.colorspace.PdfColorSpace;
import com.itextpdf.layout.Style;
import com.itextpdf.layout.element.Image;
import com.itextpdf.layout.element.Text;
import com.itextpdf.layout.properties.TextAlignment;
import static com.itextpdf.layout.properties.TextAlignment.*;
import static java.awt.SystemColor.text;
import java.io.File;
import javax.swing.text.StyleConstants.FontConstants;

public class ITextPdf {

    public static void createPara(Document doc, Paragraph name, String text, Style style, int boxHeight
                        ,int boxWidth, int x, int y, TextAlignment align){
        name = new Paragraph().add(new Text(text).addStyle(style));
        name.setHeight(boxHeight).setWidth(boxWidth).setBackgroundColor(ColorConstants.WHITE);
        doc.showTextAligned(name, x, y, align);
    }
        
    public static void createLine(Document doc, Paragraph name, int boxHeight, int boxWidth, int x, int y){
        name = new Paragraph();
        name.setHeight(boxHeight).setWidth(boxWidth).setBackgroundColor(ColorConstants.LIGHT_GRAY);
        doc.showTextAligned(name, x, y, TextAlignment.LEFT);
    }
    
    
    public static void main(String[] args) throws Exception{
        
        String path = "C:\\Users\\Pc\\Desktop\\Java\\Files\\odev.pdf";
        String imagePath = "Image\\image.jpeg"; //200x200
        
        String name = "ALEXANDER PETERS";
        
        String profession = "SOFTWARE ENGINEER";
        
        String phoneNum = "070 1935 3243";
        String email = "AlexanderPeters@teleworm.us";
        String address = "10 Grenoble Road BRENTFORD TW8 4FF";
        
        String profile = "Highly skilled and results-driven software developer with over 5 years of experience in designing, developing, and implementing innovative software solutions. Proficient in multiple programming languages including Java, Python, and JavaScript. Adept at collaborating with cross-functional teams to deliver high-quality products within tight deadlines.";
        
        String skill1 = "Visual Design";
        String skill2 = "PowerPoint";
        String skill3 = "Problem-Solving";
        String skill4 = "Social Media Marketing";        
        
        String titleWork1 = "XYZ Tech Solutions";
        String locWork1 = "San Francisco CA";
        String yearWork1 = "2019 - 2022";
        String paraWork1 = "Developed and maintained web applications using JavaScript, React, and Node.js. Collaborated with cross-functional teams to design and implement new features. Conducted code reviews and optimized application performance.";

        
        String titleWork2 = "ABC Innovations";
        String locWork2 = "New York NY";
        String yearWork2 = "2016 - 2019";
        String paraWork2 = "Designed and implemented RESTful APIs using Python and Django. Managed database systems and ensured data integrity. Worked closely with front-end developers to integrate user-facing elements.";

        
        String titleWork3 = "TechWave Inc.";
        String locWork3 = "Austin TX";
        String yearWork3 = "2014 - 2016";
        String paraWork3 = "Assisted in the development of mobile applications using Java and Kotlin. Participated in the full software development lifecycle from planning to deployment. Debugged and resolved software issues to improve application stability.";
        
        
        PdfWriter writer = new PdfWriter(path);
        PdfDocument pdoc = new PdfDocument(writer);
        Document doc = new Document(pdoc);
        
        
    //Font
        PdfFont code = PdfFontFactory.createFont(StandardFonts.COURIER_BOLD);
        PdfFont normal = PdfFontFactory.createFont(StandardFonts.COURIER);

        
        //Style
        
        Style nameStyle = new Style().setFont(code)
                .setFontSize(26);
        Style titleStyle = new Style().setFont(code)
                .setFontSize(16);
        Style normalStyle = new Style().setFont(normal)
                .setFontSize(14);
        Style smlTitleStyle = new Style().setFont(code)
                .setFontSize(15);
        Style bigTitleStyle = new Style().setFont(code)
                .setFontSize(18);
        
    
    //Paragraphs
        Paragraph nameTitle = null;
        Paragraph contactTitle = null;
        Paragraph profileTitle = null;
        Paragraph skillsTitle = null;
        Paragraph professionTitle = null;
        Paragraph workTitle = null;
        Paragraph firstWorkTitle = null;
        Paragraph secondWorkTitle = null;
        Paragraph thirdWorkTitle = null;
        Paragraph infoPara = null;
        Paragraph profilePara = null;
        Paragraph skillsPara = null;
        Paragraph firstWorkPara =null;
        Paragraph secondWorkPara = null;
        Paragraph thirdWorkPara = null;
 
        
        //Name
        createPara(doc, nameTitle, name, nameStyle, 200, 300, 430, 600, CENTER);
        
        
        //Information
        String infoTitle = "CONTACT";
        createPara(doc, contactTitle, infoTitle, titleStyle, 100, 200, 100, 490, LEFT);
        createPara(doc, infoPara, phoneNum + "\n\n" + email + "\n\n" + address, normalStyle
                , 100, 240, 15, 460, LEFT);
        
        
        //Profile
        String profTitle = "PROFILE";
        createPara(doc, profileTitle, profTitle, titleStyle, 100, 200, 100, 340, LEFT);
        createPara(doc, profilePara, profile, normalStyle, 200, 240, 15, 220, LEFT);
        
        
        //Skills
        String titleSkills = "SKILLS";
        createPara(doc, skillsTitle, titleSkills, titleStyle, 100, 200, 100, 95, LEFT);
        createPara(doc, skillsPara, "-" + skill1 + "\n\n" + "-" + skill2 + "\n\n" 
                        + "-" + skill3 + "\n\n" + "-" + skill4, normalStyle
                , 100, 200, 15, 60, LEFT);
        
        
        //Profession
        
        createPara(doc, professionTitle, profession, bigTitleStyle, 100, 200, 425, 650, CENTER);
        
        
        //Work Experience
        String titleWork = "WORK EXPERIENCE";
        createPara(doc, workTitle, titleWork, bigTitleStyle, 100, 200, 427, 560, CENTER);
        
        //Work 1
        createPara(doc, firstWorkTitle, titleWork1 + "\n" + locWork1 + "\n" + yearWork1
                            , smlTitleStyle, 100, 200, 427, 515, CENTER);
        createPara(doc, firstWorkPara, paraWork1, normalStyle, 100, 250, 427, 470, CENTER);
        
        //Work 2
        createPara(doc, secondWorkTitle, titleWork2 + "\n" + locWork2 + "\n" + yearWork2
                , smlTitleStyle, 100, 200, 427, 330, CENTER);
        createPara(doc, secondWorkPara, paraWork2, normalStyle, 100, 250, 427, 285, CENTER);
        
        //Work 3
        createPara(doc, thirdWorkTitle, titleWork3 + "\n" + locWork3 + "\n" + yearWork3
                , smlTitleStyle, 100, 200, 427, 155, CENTER);
        createPara(doc, thirdWorkPara, paraWork3, normalStyle, 100, 250, 427, 110, CENTER);
        
        
    //Lines
    
        Paragraph topLeft = null;
        Paragraph topLeft1 = null;
        Paragraph bottomLeft1 = null;
        Paragraph photoBg = null;
        Paragraph upperProf = null;
        Paragraph upperName = null;
        Paragraph upperWork = null;
        Paragraph btwnWork1 = null;         
        Paragraph btwnWork2 = null; 
        Paragraph btwnWork3 = null;
        Paragraph btwnWork4 = null;
        Paragraph bottomPage = null;
        Paragraph bottomPage2 = null;
                
        createLine(doc, topLeft, 2, 240, 15, 450);
        createLine(doc, topLeft1, 2, 240, 15, 600);
        createLine(doc, bottomLeft1, 2, 240, 15, 200);
        createLine(doc, photoBg, 300, 270, 0, 598);
        createLine(doc, upperProf, 2, 240, 300, 765);
        createLine(doc, upperName, 100, 600, 200, 810);
        createLine(doc, upperWork, 2, 210, 320, 670);
        createLine(doc, btwnWork1, 4, 4, 410, 450);
        createLine(doc, btwnWork2, 4, 4, 430, 450);
        createLine(doc, btwnWork3, 4, 4, 410, 270);
        createLine(doc, btwnWork4, 4, 4, 430, 270);
        createLine(doc, bottomPage, 30, 600, 0, 0);
        createLine(doc, bottomPage2, 20, 300, 300, 30);
        
        
    //Image
    
        ImageData data = ImageDataFactory.create(imagePath);
        Image image = new Image(data);

        doc.add(image);

        doc.close();
        
    }
}
