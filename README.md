# cadastro_java_
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

import javax.swing.JOptionPane;

public class Cadastro {

	public static void main(String[] args) {
		int opc = 0;
		String vet[] = new String[4];
		String texto[] = { "Digite código do cliente", "Digite nome do cliente", "Digite CEP do cliente",
				"Digite telefone do cliente" };
		String codigo, nome, cep, telefone;

		while (opc != 5) {
			opc = Integer.parseInt(
					JOptionPane.showInputDialog("OPÇÕES\n1-Incluir\n2-Alterar\n3-Excluir\n4-Gravar Arquivo\n5-Sair"));

			switch (opc) {
			case 1:
				// opção 1
				for (int x = 0; x < 4; x++) {
					vet[x] = JOptionPane.showInputDialog(texto[x]);
				}
				break;

			case 2:
				int op2;
				op2 = Integer
						.parseInt(JOptionPane.showInputDialog("Escolha a opção:\n0-Codigo\n1-Nome\n2-CEP\n3-Telefone"));
				switch (op2) {
				case 0:
					vet[0] = JOptionPane.showInputDialog(texto[0], vet[0]);
					break;
				case 1:
					vet[1] = JOptionPane.showInputDialog(texto[1], vet[1]);
					break;
				case 2:
					vet[2] = JOptionPane.showInputDialog(texto[2], vet[2]);
					break;
				case 3:
					vet[3] = JOptionPane.showInputDialog(texto[3], vet[3]);
					break;
				}// fim do switch
				break;

			case 3:
				int op3;
				op3 = Integer.parseInt(JOptionPane
						.showInputDialog("Escolha o que deseja excluir:\n0-Codigo\n1-Nome\n2-CEP\n3-Telefone"));
				switch (op3) {
				case 0:
					vet[0] = "";
					JOptionPane.showMessageDialog(null, "Código excluído com sucesso!");
					break;
				case 1:
					vet[1] = "";
					JOptionPane.showMessageDialog(null, "Nome excluído com sucesso!");
					break;
				case 2:
					vet[2] = "";
					JOptionPane.showMessageDialog(null, "CEP excluído com sucesso!");
					break;
				case 3:
					vet[3] = "";
					JOptionPane.showMessageDialog(null, "Telefone excluído com sucesso!");
					break;
				}// fim do switch
				break;
			case 4:
				File arquivo = new File("c:\\Users\\Professor\\Downloads\\Cadastro.txt");
				String Gravar=vet[0]+"\n"+vet[1]+"\n"+vet[2]+"\n"+vet[3]+"\n";
				
				
				try {
					if (!arquivo.exists()) {
					//cria um arquivo (vazio)
					arquivo.createNewFile();
					}
					//caso seja um diretório, é possível listar seus arquivos e diretórios
					File[] arquivos = arquivo.listFiles();
					//escreve no arquivo
					FileWriter fw = new FileWriter(arquivo, true);
					BufferedWriter bw = new BufferedWriter(fw);
					bw.write(Gravar);
					bw.newLine();
					bw.close();
					fw.close();
					//faz a leitura do arquivo
					FileReader fr = new FileReader(arquivo);
					BufferedReader br = new BufferedReader(fr);
					//enquanto houver mais linhas
					while (br.ready()) {
					//lê a proxima linha
					String linha = br.readLine();
					//faz algo com a linha
					System.out.println(linha);
					}
					br.close();
					fr.close();
					} catch (IOException ex) {
					ex.printStackTrace();
					}
				JOptionPane.showMessageDialog
				(null, "Arquivo gravado com sucesso. Verifique sua pasta 'Downloads'");
				break;

			case 5:
				JOptionPane.showMessageDialog(null, "Programa finalizado com sucesso!");
				break;
			default:
				JOptionPane.showMessageDialog(null, "Opção Não Existe. Tente Novamente!");

			}// fim do switch

		} // fim do while

	}

}
